# Tubely

A backend file server written in Go that stores and serves video files using
AWS S3, with AWS CloudFront as a CDN layer for fast, cached delivery. Tubely
also handles video thumbnails and associated metadata.

## Features

- Upload and retrieve video files via a REST API
- Generate and serve video thumbnails
- Store and manage video metadata (title, description, etc.)
- Persistent storage backed by AWS S3
- Global content delivery via AWS CloudFront
- Signed URLs / distribution config for secure, performant access

## Tech Stack

- Go
- AWS S3
- AWS CloudFront
- AWS IAM (least-privilege access policies)

## Setup

### Prerequisites

- An AWS account
- An S3 bucket
- A CloudFront distribution pointed at that bucket
- IAM user/role with permissions scoped to S3 access

### Environment Variables

| Variable             | Description                          |
|----------------------|---------------------------------------|
| `S3_BUCKET`          | Name of your S3 bucket               |
| `S3_REGION`          | AWS region of the bucket             |
| `CLOUDFRONT_DOMAIN`  | Your CloudFront distribution domain  |
| `AWS_ACCESS_KEY_ID`  | IAM access key (not committed)       |
| `AWS_SECRET_ACCESS_KEY` | IAM secret key (not committed)    |

### Running locally

\`\`\`bash
go run main.go
\`\`\`

## API Overview

- `POST /videos` - upload a new video and its metadata
- `POST /videos/{id}/thumbnail` - upload a thumbnail for a video
- `GET /videos/{id}` - retrieve video metadata and playback URL

## About the name

Tubely is a lighthearted nod to video-sharing platforms, reflecting its
purpose: storing and streaming video content efficiently.

## Notes

Tubely was built as part of the Boot.dev "Learn File Servers and CDNs with
S3 and CloudFront" course. AWS resources used during development (S3
buckets, CloudFront distribution, IAM roles/users) have since been deleted
to avoid ongoing charges, so the live demo is no longer active.