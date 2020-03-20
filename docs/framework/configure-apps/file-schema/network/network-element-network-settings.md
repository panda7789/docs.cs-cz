---
title: <network> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154813"
---
# <a name="network-element-network-settings"></a>\<prvek síťové> (Nastavení sítě)
Konfiguruje možnosti sítě pro externí server SMTP (SMTP) (Simple Mail Transport Protocol).  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailNastavení>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<síťová>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<network  
  clientDomain="string"
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"
  password="string"  
  port="integer"
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`clientDomain`|Určuje název domény klienta, který má být používán v počátečním požadavku protokolu SMTP pro připojení k poštovnímu serveru SMTP. Výchozí hodnota je název localhost místního počítače odesílajícího požadavek.|  
|`defaultCredentials`|Určuje, zda mají být pro přístup k poštovnímu serveru SMTP pro transakce SMTP použita výchozí pověření uživatele. Výchozí hodnota je `false`.|  
|`enableSsl`|Určuje, zda se ssl používá pro přístup k poštovnímu serveru SMTP. Výchozí hodnota je `false`.|  
|`host`|Určuje název hostitele poštovního serveru SMTP, který má být používán pro transakce SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`password`|Určuje heslo, které má být používáno pro ověřování poštovního serveru SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`port`|Určuje číslo portu, které se má použít pro připojení k poštovnímu serveru SMTP. Výchozí hodnota je 25.|  
|`targetName`|Určuje název poskytovatele služeb (SPN), který se má použít pro ověřování při použití rozšířené ochrany pro transakce SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`userName`|Určuje uživatelské jméno, které má být používáno pro ověřování poštovního serveru SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<smtp> Element (Nastavení sítě)](smtp-element-network-settings.md)|Konfiguruje možnosti odesílání pošty protokolu SMTP (SMTP) protokolu SMTP.|  
  
## <a name="remarks"></a>Poznámky  
 Některé servery SMTP vyžadují, abyste se před použitím ověřili na serveru. Pokud se chcete ověřit pomocí výchozích síťových pověření `defaultCredentials` na `true`hostiteli, nastavte atribut na . Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> lze získat aktuální hodnotu atributu `defaultCredentials` z příslušných konfiguračních souborů.  
  
 K ověření na serveru SMTP můžete také použít základní ověřování (uživatelské jméno a heslo). Chcete-li použít tuto možnost, musíte zadat platné uživatelské jméno a heslo pro zadaný server SMTP.  
  
> [!NOTE]
> Základní ověřování `userName` odešle hodnoty a `password` na server nezašifrované. Kdokoli, kdo sleduje provoz v síti, může zobrazit vaše pověření a použít je k připojení k serveru. Měli byste zvážit použití bezpečnějšího mechanismu ověřování, například Kerberos nebo NT LAN Manager (NTLM.) Pokud `defaultCredentials` `true`je , protokol Kerberos nebo NTLM bude použit, pokud server podporuje tyto protokoly.  
  
 Základní možnosti ověřování a výchozí chrup síťových pověření se vzájemně vylučují. Pokud nastavíte `defaultCredentials` `true` a zadáte uživatelské jméno a heslo, použije se výchozí síťové pověření a základní ověřovací data budou ignorována.  
  
 Pro základní ověřování, `userName`pokud zadáte , `password` měli byste také zadat a pro ověřování sami na poštovní server.  
  
 Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> lze získat aktuální hodnotu atributu `userName` z příslušných konfiguračních souborů. Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> lze získat aktuální hodnotu atributu `password` z příslušných konfiguračních souborů. Atribut `password` by obvykle nebyl zadán do konfiguračních souborů z bezpečnostních důvodů.  
  
 Atribut `clientDomain` změní název domény klienta použitý v počátečním požadavku protokolu SMTP na server SMTP. Atribut `clientDomain` lze nastavit na plně kvalifikovaný název domény místního počítače, nikoli název localhost, který se používá ve výchozím nastavení. To poskytuje větší soulad se standardy protokolu SMTP. Výchozí hodnota je název localhost místního počítače odesílajícího požadavek. Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> lze získat aktuální hodnotu atributu `clientDomain` z příslušných konfiguračních souborů.  
  
 Atribut `targetName` se používá pro ověřování při použití rozšířené ochrany. Výchozí hodnota je ve tvaru "SMTPSVC/\< \<host>", kde> hostitele je název hostitele poštovního serveru SMTP. Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> lze získat aktuální hodnotu atributu `targetName` z příslušných konfiguračních souborů.  
  
 Atribut `enableSsl` určuje, zda se ssl používá pro přístup k poštovnímu serveru SMTP. Třída <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> podporuje pouze rozšíření služby SMTP pro zabezpečené smtp přes zabezpečení transportní vrstvy, jak je definováno v RFC 3207. V tomto režimu začíná relace SMTP na nešifrovaném kanálu, poté klient serveru vydá příkaz STARTTLS, aby se přepnul na zabezpečenou komunikaci pomocí ssl. Další informace naleznete v tématu RFC 3207 publikovaná skupinou IETF (Internet Engineering Task Force).  
  
 Alternativní metoda připojení je místo, kde je před odesláním všech příkazů protokolu vytvořena relace SSL. Tato metoda připojení se někdy nazývá SMTPS a ve výchozím nastavení používá port 465. Tato alternativní metoda připojení pomocí ssl není aktuálně podporována.  
  
 Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> lze získat aktuální hodnotu atributu `enableSsl` z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje příslušné parametry SMTP pro odesílání e-mailů pomocí výchozích síťových pověření.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
