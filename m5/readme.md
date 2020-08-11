# Automated Deployments with CloudFormation

## [Application stack template](app-stack.json)

Deploys the following in a virtual private cloud (VPC) (created by the [network stack template](network-stack.json)):
- Auto Scaling group in the public web tier
- Internet-facing application load balancer for the web tier
- Auto Scaling group in the application tier
- Internal application load balancer for the application tier
- Security groups

## [Network stack nested template](network-stack.json)

Deploys the following:
- A virtual private cloud (VPC)
- Two public subnets in different zones
- Two private subnets in different zones
- Internet gateway
- NAT gateway

## Region considerations

If you intend to deploy these templates outside of the us-east-1 region, you'll need to change the following:
- All references to us-east-1 in [network-stack.json](network-stack.json)
- The AMI ID in [app-stack.json](app-stack.json)
- Add `--region [region-code]` to the end of the `cfn-signal` command in [app-stack.json](app-stack.json)
