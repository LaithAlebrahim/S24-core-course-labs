# Terraform
- you just need to go into the required directory and write the following command to run the Terraform project:
- Also you need to add your ssh credentials to the environment
```bash
terrafrom int
terraform apply 
```
- To show the output of the Terraform:
```bash
terraform show 
```

# docker_container.nginx:
resource "docker_container" "nginx" {
    attach                                      = false
    command                                     = [
        "nginx",
        "-g",
        "daemon off;",
    ]
    container_read_refresh_timeout_milliseconds = 15000
    cpu_shares                                  = 0
    entrypoint                                  = [
        "/docker-entrypoint.sh",
    ]
    env                                         = []
    hostname                                    = "99803a5cf924"
    id                                          = "99803a5cf9243013e4a0266b3b9c7921350d045412846696d87784dc8048cf90"
    image                                       = "sha256:e4720093a3c1381245b53a5a51b417963b3c4472d3f47fc301930a4f3b17666a"
    init                                        = false
    ipc_mode                                    = "private"
    log_driver                                  = "json-file"
    logs                                        = false
    max_retry_count                             = 0
    memory                                      = 0
    memory_swap                                 = 0
    must_run                                    = true
    name                                        = "app_python"
    network_data                                = [
        {
            gateway                   = "172.17.0.1"
            global_ipv6_address       = ""
            global_ipv6_prefix_length = 0
            ip_address                = "172.17.0.2"
            ip_prefix_length          = 16
            ipv6_gateway              = ""
            mac_address               = "02:42:ac:11:00:02"
            network_name              = "bridge"
        },
    ]
    network_mode                                = "default"
    privileged                                  = false
    publish_all_ports                           = false
    read_only                                   = false
    remove_volumes                              = true
    restart                                     = "no"
    rm                                          = false
    runtime                                     = "runc"
    security_opts                               = []
    shm_size                                    = 64
    start                                       = true
    stdin_open                                  = false
    stop_signal                                 = "SIGQUIT"
    stop_timeout                                = 0
    tty                                         = false
    wait                                        = false
    wait_timeout                                = 60

    ports {
        external = 8000
        internal = 80
        ip       = "0.0.0.0"
        protocol = "tcp"
    }
}

# docker_image.nginx:
resource "docker_image" "nginx" {
    id           = "sha256:e4720093a3c1381245b53a5a51b417963b3c4472d3f47fc301930a4f3b17666anginx"
    image_id     = "sha256:e4720093a3c1381245b53a5a51b417963b3c4472d3f47fc301930a4f3b17666a"
    keep_locally = false
    name         = "nginx"
    repo_digest  = "nginx@sha256:c26ae7472d624ba1fafd296e73cecc4f93f853088e6a9c13c0d52f6ca5865107"
}


Outputs:

container_id = "99803a5cf9243013e4a0266b3b9c7921350d045412846696d87784dc8048cf90"
image_id = "sha256:e4720093a3c1381245b53a5a51b417963b3c4472d3f47fc301930a4f3b17666anginx"




# aws_instance.app_server:
resource "aws_instance" "app_server" {
    ami                                  = "ami-0faab6bdbac9486fb"
    arn                                  = "arn:aws:ec2:eu-central-1:282160524889:instance/i-0f4a12855cf37e05a"
    associate_public_ip_address          = true
    availability_zone                    = "eu-central-1a"
    cpu_core_count                       = 1
    cpu_threads_per_core                 = 1
    disable_api_stop                     = false
    disable_api_termination              = false
    ebs_optimized                        = false
    get_password_data                    = false
    hibernation                          = false
    id                                   = "i-0f4a12855cf37e05a"
    instance_initiated_shutdown_behavior = "stop"
    instance_state                       = "running"
    instance_type                        = "t2.micro"
    ipv6_address_count                   = 0
    ipv6_addresses                       = []
    monitoring                           = false
    placement_partition_number           = 0
    primary_network_interface_id         = "eni-02e6e462514ca8c44"
    private_dns                          = "ip-172-31-22-167.eu-central-1.compute.internal"
    private_ip                           = "172.31.22.167"
    public_dns                           = "ec2-18-193-115-235.eu-central-1.compute.amazonaws.com"
    public_ip                            = "18.193.115.235"
    secondary_private_ips                = []
    security_groups                      = [
        "default",
    ]
    source_dest_check                    = true
    subnet_id                            = "subnet-0626d7c68fc9f281b"
    tags                                 = {
        "Name" = "terrafom-testing"
    }
    tags_all                             = {
        "Name" = "terrafom-testing"
    }
    tenancy                              = "default"
    user_data_replace_on_change          = false
    vpc_security_group_ids               = [
        "sg-0c522df23a8429e2d",
    ]

    capacity_reservation_specification {
        capacity_reservation_preference = "open"
    }

    cpu_options {
        core_count       = 1
        threads_per_core = 1
    }

    credit_specification {
        cpu_credits = "standard"
    }

    enclave_options {
        enabled = false
    }

    maintenance_options {
        auto_recovery = "default"
    }

    metadata_options {
        http_endpoint               = "enabled"
        http_put_response_hop_limit = 1
        http_tokens                 = "optional"
        instance_metadata_tags      = "disabled"
    }

    private_dns_name_options {
        enable_resource_name_dns_a_record    = false
        enable_resource_name_dns_aaaa_record = false
        hostname_type                        = "ip-name"
    }

    root_block_device {
        delete_on_termination = true
        device_name           = "/dev/sda1"
        encrypted             = false
        iops                  = 100
        tags                  = {}
        throughput            = 0
        volume_id             = "vol-08f7a667c73fdc27a"
        volume_size           = 8
        volume_type           = "gp2"
    }
}


Outputs:

aws_instance_IP = "18.193.115.235"


# github_branch_default.main:
resource "github_branch_default" "main" {
    branch     = "main"
    etag       = "W/\"e713dca9875043acdeae4f0f78b9af6044123634492c3d1d4aab338c783583fb\""
    id         = "test-terraform"
    rename     = false
    repository = "test-terraform"
}

# github_branch_protection.default:
resource "github_branch_protection" "default" {
    allows_deletions                = false
    allows_force_pushes             = false
    enforce_admins                  = true
    id                              = "BPR_kwDOLY2vw84C0v8X"
    lock_branch                     = false
    pattern                         = "main"
    repository_id                   = "test-terraform"
    require_conversation_resolution = true
    require_signed_commits          = false
    required_linear_history         = false

    required_pull_request_reviews {
        dismiss_stale_reviews           = false
        require_code_owner_reviews      = false
        require_last_push_approval      = false
        required_approving_review_count = 1
        restrict_dismissals             = false
    }
}

# github_repository.test-terraform:
resource "github_repository" "test-terraform" {
    allow_auto_merge            = false
    allow_merge_commit          = true
    allow_rebase_merge          = true
    allow_squash_merge          = true
    allow_update_branch         = false
    archived                    = false
    auto_init                   = true
    default_branch              = "main"
    delete_branch_on_merge      = false
    description                 = "Test terraform"
    etag                        = "W/\"e713dca9875043acdeae4f0f78b9af6044123634492c3d1d4aab338c783583fb\""
    full_name                   = "LaithAlebrahim/test-terraform"
    git_clone_url               = "git://github.com/LaithAlebrahim/test-terraform.git"
    gitignore_template          = "VisualStudio"
    has_discussions             = false
    has_downloads               = false
    has_issues                  = true
    has_projects                = false
    has_wiki                    = true
    html_url                    = "https://github.com/LaithAlebrahim/test-terraform"
    http_clone_url              = "https://github.com/LaithAlebrahim/test-terraform.git"
    id                          = "test-terraform"
    is_template                 = false
    license_template            = "mit"
    merge_commit_message        = "PR_TITLE"
    merge_commit_title          = "MERGE_MESSAGE"
    name                        = "test-terraform"
    node_id                     = "R_kgDOLY2vww"
    private                     = false
    repo_id                     = 764260291
    squash_merge_commit_message = "COMMIT_MESSAGES"
    squash_merge_commit_title   = "COMMIT_OR_PR_TITLE"
    ssh_clone_url               = "git@github.com:LaithAlebrahim/test-terraform.git"
    svn_url                     = "https://github.com/LaithAlebrahim/test-terraform"
    topics                      = []
    visibility                  = "public"
    vulnerability_alerts        = false
    web_commit_signoff_required = false

    security_and_analysis {
        secret_scanning {
            status = "disabled"
        }
        secret_scanning_push_protection {
            status = "disabled"
        }
    }
}


Outputs:

default_branch = "main"
repository_id = "test-terraform"
repository_name = "test-terraform"


### Overall Best Practices

* Use the `terraform plan` command to preview the changes before applying them.
* Use the `terraform apply` command to apply the changes.
* Handle sensitive data with care.
* Utilize `terraform show` to display the outputs.