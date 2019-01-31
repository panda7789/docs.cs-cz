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
ms.openlocfilehash: 67743ccf2fa14117814160aeb7624c2be4eea364
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257860"
---
# <a name="network-element-network-settings"></a>\<Síť > – Element (nastavení sítě)
Konfiguruje možnosti sítě pro externí server Simple Mail Transport Protocol (SMTP).  
  
 \<Konfigurace >  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<network>  
  
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
|`clientDomain`|Určuje název domény klienta pro použití v prvotní žádosti protokolu SMTP pro připojení k poštovnímu serveru SMTP. Výchozí hodnota je localhost název místního počítače, které odesílá požadavek.|  
|`defaultCredentials`|Určuje, zda by měl použít výchozí pověření uživatele pro přístup k poštovnímu serveru SMTP pro transakce SMTP. Výchozí hodnota je `false`.|  
|`enableSsl`|Určuje, zda se používá protokol SSL pro přístup k poštovnímu serveru SMTP. Výchozí hodnota je `false`.|  
|`host`|Určuje název hostitele poštovního serveru SMTP pro transakce SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`password`|Určuje heslo pro účely ověření k poštovnímu serveru SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`port`|Udává číslo portu pro připojení k poštovnímu serveru SMTP. Výchozí hodnota je 25.|  
|`targetName`|Určuje název zprostředkovatele služby (SPN) pro účely ověření při používání rozšířené ochrany pro transakce SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`userName`|Určuje uživatelské jméno pro účely ověření k poštovnímu serveru SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<SMTP > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Konfiguruje možnosti pro odesílání pošty Simple Mail Transport Protocol (SMTP).|  
  
## <a name="remarks"></a>Poznámky  
 Některé servery SMTP vyžadují ověření sami na server před použitím. Pokud chcete provést ověření pomocí výchozích síťových přihlašovacích údajů na hostiteli, nastavte `defaultCredentials` atribut `true`. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `defaultCredentials` atribut z příslušných konfiguračních souborů.  
  
 Můžete také použít základní ověřování (uživatelské jméno a heslo) k sami ověření serveru SMTP. Pokud chcete použít tuto možnost, musíte zadat platné uživatelské jméno a heslo pro zadaný server SMTP.  
  
> [!NOTE]
>  Základní ověřování odešle `userName` a `password` hodnoty server v nezašifrované. Kdokoli na nich monitorování síťového provozu můžete zobrazit svoje přihlašovací údaje a použít pro připojení k serveru. Měli byste zvážit použití bezpečnější mechanismu ověřování, jako je protokol Kerberos nebo NT LAN Manager (NTLM). Pokud `defaultCredentials` je `true`, Kerberos nebo NTLM bude použit, pokud server podporuje tyto protokoly.  
  
 Základní ověřování a výchozí síťové přihlašovací údaje možnosti se vzájemně vylučují. Pokud nastavíte `defaultCredentials` k `true` a zadejte uživatelské jméno a heslo, se používá výchozí pověření sítě a data základního ověřování, je ignorován.  
  
 Pro základní ověřování, pokud zadáte `userName`, byste zadat také `password` ověřování sami poštovním serveru.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `userName` atribut z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `password` atribut z příslušných konfiguračních souborů. A `password` by normálně je třeba zadat atribut v konfiguračních souborech z bezpečnostních důvodů.  
  
 `clientDomain` Atribut změní název domény klienta použitý v původní žádost protokolu SMTP na serveru SMTP. `clientDomain` Atribut může být nastaven plně kvalifikovaný název domény z místního počítače, nikoli název localhost, který se používá ve výchozím nastavení. To poskytuje větší dodržování standardů protokol SMTP. Výchozí hodnota je localhost název místního počítače, které odesílá požadavek. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `clientDomain` atribut z příslušných konfiguračních souborů.  
  
 `targetName` Atribut se používá k ověřování při použití rozšířenou ochranu. Výchozí hodnota je ve formátu "SMTPSVC /\<hostitele >" kde \<hostitele > je název hostitele serveru SMTP, e-mailu. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `targetName` atribut z příslušných konfiguračních souborů.  
  
 `enableSsl` Atribut určuje, zda se používá protokol SSL pro přístup k poštovnímu serveru SMTP. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Třídy podporuje pouze rozšíření služby SMTP pro zabezpečený protokol SMTP přes Transport Layer Security jak jsou definovány v dokumentu RFC 3207. V tomto režimu SMTP relace začíná nešifrovaný kanál a pak je vydán příkaz STARTTLS klienta k serveru a přepnout na zabezpečenou komunikaci pomocí protokolu SSL. Najdete v dokumentu RFC 3207 publikovaná pomocí Engineering Task Force IETF (Internet) pro další informace.  
  
 Metodu připojení je, kde relace SSL pokládáme stav, ještě před zahájením před libovolného protokolu pro odeslání příkazy. Tato metoda připojení se někdy označuje jako SMTPS a ve výchozím nastavení používá port 465. Tato metoda připojení pomocí protokolu SSL se momentálně nepodporuje.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `enableSsl` atribut z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje příslušné parametry protokolu SMTP k odesílání e-mailů pomocí výchozích síťových přihlašovacích údajů.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
