# Backup Automation Template

NX-OS와 IOS 장비의 `running-config`를 텍스트 파일로 저장한 뒤 `copy running-config startup-config`를 실행하고, 실행 결과를 로그 파일로 남기는 단순 백업 템플릿이다.

## Files

- `inventory.ini`: 장비 접속 정보 템플릿
- `backup_nxos.yml`: NX-OS 장비 백업
- `backup_ios.yml`: IOS 장비 백업
- `backup_all.yml`: NX-OS와 IOS 백업 순차 실행
- `backups/`: 백업 텍스트 파일 출력 위치
- `logs/`: 저장 명령 실행 로그 출력 위치

## Usage

1. `inventory.ini`의 장비명, 관리 IP, 계정 정보를 실제 환경에 맞게 교체한다.
2. 필요한 컬렉션을 설치한다.

```bash
ansible-galaxy collection install -r requirements.yml
```

3. 백업 플레이북을 실행한다.

```bash
ansible-playbook backup_all.yml
ansible-playbook backup_nxos.yml
ansible-playbook backup_ios.yml
```

운영 환경에서는 `ansible_password`와 `ansible_become_password`를 직접 저장하지 말고 Ansible Vault 사용을 권장한다.
