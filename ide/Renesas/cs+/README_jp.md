# wolfSSH �V���v�� SSH �T�[�o �Z�b�g�A�b�v�K�C�h

���̃f���͈ȉ��̊��Ńe�X�g���Ă��܂��B  

* Renesas : CS+ v8.01
* Board   : Alpha Project AP-RX71M-0A w/ Sample program v2.0
* wolfSSL : 4.0.0
* wolfSSH : 1.3.1

##�Z�b�g�A�b�v�菇�F
### �P �\�t�g�E�F�A�̓���

- AP�{�[�h�t���̃\�t�g�E�F�A�ꎮ��K���ȃt�H���_�[���ɉ𓀂��܂��B  
- �����t�H���_�[����wolfssl�ꎮ���𓀂��܂��B
- �����t�H���_�[����wolfssh�ꎮ���𓚂��܂��B
### �Q wolfSSL�y��wolfSSH�̃Z�b�g�A�b�v

- CS+�ɂ�wolfssh\ide\Renesas\cs+\����wolfssl_lib\wolfssl_lib.mtpj���J��  
  wolfSSL���C�u�����[�̃r���h�����܂��B
- CS+�ɂ�wolfssh\ide\Renesas\cs+\����wolfssh_lib\wolfssj_lib.mtpj���J��  
  wolfSSh���C�u�����[�̃r���h�����܂��B
- �����t�H���_�̉���demo_server.mtpj���J���A�f���v���O�����̃r���h�����܂��B  
  ���̃v���O���������C�u�����[�`���Ńr���h����܂��B

### �R AlphaProject���̃Z�b�g�A�b�v
�f����ap_rx71m_0a_sample_cs\Sample\ap_rx71m_0a_usbfunc_sample_cs�t�H���_����  
ap_rx71m_0a_usbfunc_sample_cs.mtpj�v���W�F�N�g�𗘗p���܂��B

- ap_rx71m_0a_sample_cs\Sample\ap_rx71m_0a_ether_sample_cs\src�t�H���_����AP_RX71M_0A.c�t�@�C�����J���A  
  UsbfInit()�̉���wolfSSL_init()��}�����܂��B

```
        CanInit();
        SciInit();
        EthernetAppInit();
        UsbfInit();
        wolfSSL_init(); <- ���̍s��}��
```
- ap_rx71m_0a_sample_cs\Sample\ap_rx71m_0a_usbfunc_sample_cs\src\smc_gen\r_config\r_bsp_config.h  
  ���J���A�X�^�b�N�T�C�Y�ƃq�[�v�T�C�Y���ȉ��̂悤�ɐݒ肵�܂��B  
�@154�s�� #pragma stacksize su=0x2000  
�@175�s�� #define BSP_CFG_HEAP_BYTES  (0xa000)  

- IP�A�h���X�̃f�t�H���g�l�͈ȉ��̂悤�ɂȂ��Ă��܂��B  
�@�K�v������΁ASample\ap_rx71m_0a_ether_sample_cs\src\tcp_sample\config_tcpudp.c
�@����139�s�ڂ���̒�`��ύX���܂��B

```
       #define MY_IP_ADDR0     192,168,1,200           /* Local IP address  */
       #define GATEWAY_ADDR0   192,168,1,254           /* Gateway address (invalid if all 0s) */
       #define SUBNET_MASK0    255,255,255,0           /* Subnet mask  */
```
- CS+��ap_rx71m_0a_usbfunc_sample_cs.mtpj�v���W�F�N�g���J���AwolfSSL�AwolfSSH�y�уf�����C�u������  
�@�o�^���܂��BCC-RX(�r���h�c�[��)->�����N�E�I�v�V�����^�u->�g�p���郉�C�u������  
�@�ȉ��̓�̃t�@�C����o�^���܂��B

 - CC-RX(�r���h�c�[��)->���C�u�����[�W�F�l���[�V�����^�u->���C�u�����[�\�����uC99�v�ɁA  
    ctype.h��L���ɂ�����u�͂��v�ɐݒ肵�܂��B

- �v���W�F�N�g�̃r���h�A�^�[�Q�b�g�ւ̃_�E�����[�h�������̂��A�\��->�f�o�b�O�E�R���\�[��  
�@����R���\�[����\�������܂��B���s���J�n����ƃR���\�[���Ɉȉ��̕\�����o�͂���܂��B
```
    Start server_test
```
- �V���v�� wolfSSH �T�[�o�́A50000�Ԃ̃|�[�g���J���đ҂��܂��B�T�[�o�ւ́AwolfSSH�ɕt�T���v���N���C�A���g��  
�g���Ĉȉ��̂悤�ɐڑ����邱�Ƃ��ł��܂��B
```
    $ ./examples/client/client -h 192.168.1.200 -p 50000 -u jill
    Sample public key check callback
    public key = 0x55a0890864ea
    public key size = 279
    ctx = You've been sampled!
    Password: <---- input "upthehill"
    Server said: Hello, wolfSSH!
```

##�@�T�|�[�g
�T�|�[�g���K�v�ȏꍇ�́A[support@wolfssl.com](mailto:support@wolfssl.com)�ւ��A�����������B

�ȏ�
