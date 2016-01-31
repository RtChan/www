This is a Test Page
=============

## S1 这是H2标题



### S1.1 这是H3标题

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
> 
> > This is a blockquote in the blockquote.
>

Use the `printf()` function.

### S1.2 this is h3

Here is an example of Code Block:

```Cpp
// PC_ClientDlg.cpp : 实现文件
//

#include "stdafx.h"

#ifdef _DEBUG
#define new DEBUG_NEW
#endif

// CPC_ClientDlg 对话框

CPC_ClientDlg::CPC_ClientDlg(CWnd* pParent /*=NULL*/)
    : CDialogEx(IDD_PC_CLIENT_DIALOG, pParent)
    , m_clientid(0)
{
    m_hIcon = AfxGetApp()->LoadIcon(IDR_MAINFRAME);
}

void CPC_ClientDlg::DoDataExchange(CDataExchange* pDX)
{
    CDialogEx::DoDataExchange(pDX);
    DDX_Text(pDX, IDC_EDIT_SERVERID, m_clientid);
    DDX_Control(pDX, IDC_EDIT_EVENT, m_event);
    DDX_Control(pDX, IDC_COMBO_SERIALPORT, m_combo);
}

BEGIN_MESSAGE_MAP(CPC_ClientDlg, CDialogEx)
    ON_WM_PAINT()
    ON_WM_QUERYDRAGICON()
    ON_MESSAGE(WM_COMM_RXCHAR, OnComm)	// SerialPort消息映射
    ON_BN_CLICKED(ID_BUTTON_RUN, &CPC_ClientDlg::OnBnClickedButtonRun)
    ON_CBN_SELCHANGE(IDC_COMBO_SERIALPORT, &CPC_ClientDlg::OnCbnSelchangeComboSerialport)
    ON_BN_CLICKED(IDCANCEL, &CPC_ClientDlg::OnBnClickedCancel)
END_MESSAGE_MAP()
```    

## S2 this is h2

+ I need to make this page too long.
+ I need to make this page too long.

|ITEMS|PRICE|QUANTITY|
|-----|:----:|:------:|
|APPLE|FREE|1|
|BEAR|$10.0|1|

### S2.1 FOR MATH
$$E=mc^2$$

### S2.2 Picture
![Bridge](imgs/bridge.jpg)
