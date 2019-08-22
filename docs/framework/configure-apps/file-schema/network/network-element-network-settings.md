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
ms.openlocfilehash: 40d89f7bd7a1f4a38a1c4030a86405e09c497899
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659317"
---
# <a name="network-element-network-settings"></a>\<Network > – element (nastavení sítě)
Nakonfiguruje možnosti sítě pro externí server SMTP (Simple Mail Transport Protocol).  
  
 \<> Konfigurace  
\<system.net>  
\<mailSettings >  
\<smtp>  
\<> sítě  
  
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
|`clientDomain`|Určuje název domény klienta, který má být použit v počátečním požadavku protokolu SMTP pro připojení k poštovnímu serveru SMTP. Výchozí hodnota je název localhost místního počítače odesílajícího požadavek.|  
|`defaultCredentials`|Určuje, zda mají být pro přístup k poštovnímu serveru SMTP pro transakce SMTP použity přihlašovací údaje výchozího uživatele. Výchozí hodnota je `false`.|  
|`enableSsl`|Určuje, zda se pro přístup k poštovnímu serveru SMTP používá protokol SSL. Výchozí hodnota je `false`.|  
|`host`|Určuje název hostitele poštovního serveru SMTP, který se má použít pro transakce SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`password`|Určuje heslo, které se má použít pro ověřování na poštovním serveru SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`port`|Určuje číslo portu, který se má použít pro připojení k poštovnímu serveru SMTP. Výchozí hodnota je 25.|  
|`targetName`|Určuje název poskytovatele služeb (SPN), který se má použít pro ověřování při použití rozšířené ochrany pro transakce SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`userName`|Určuje uživatelské jméno, které se má použít pro ověřování na poštovním serveru SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> elementu SMTP (nastavení sítě)](smtp-element-network-settings.md)|Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).|  
  
## <a name="remarks"></a>Poznámky  
 Některé servery SMTP vyžadují, abyste se před použitím ověřili na server. Pokud se chcete ověřit pomocí výchozích síťových přihlašovacích údajů na hostiteli, nastavte `defaultCredentials` atribut na. `true` Vlastnost lze použít k získání aktuální hodnoty `defaultCredentials` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>  
  
 K ověření vašeho vlastního serveru SMTP můžete použít také základní ověřování (uživatelské jméno a heslo). Chcete-li použít tuto možnost, je nutné zadat platné uživatelské jméno a heslo pro zadaný server SMTP.  
  
> [!NOTE]
>  Základní ověřování odesílá `userName` hodnoty a `password` na server nešifrovaný. Kdokoli, kdo sleduje síťový provoz, může zobrazit vaše přihlašovací údaje a použít je k připojení k serveru. Měli byste zvážit použití bezpečnějšího mechanismu ověřování, jako je například Kerberos nebo NT LAN Manager (NTLM). Pokud `defaultCredentials` je`true`, použije se protokol Kerberos nebo NTLM, pokud server tyto protokoly podporuje.  
  
 Možnosti základního ověřování a výchozích síťových přihlašovacích údajů se vzájemně vylučují. Pokud nastavíte `defaultCredentials` `true` a zadáte uživatelské jméno a heslo, použije se výchozí síťová pověření a data základního ověřování se ignorují.  
  
 Pro základní ověřování Pokud zadáte `userName`, měli byste taky `password` určit, jestli se má na poštovní server sami ověřit.  
  
 Vlastnost lze použít k získání aktuální hodnoty `userName` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `password` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Z bezpečnostních důvodů se atributvkonfiguračníchsouborechobvyklenezadá.`password`  
  
 `clientDomain` Atribut změní název domény klienta použitý v počátečním požadavku protokolu SMTP na server SMTP. `clientDomain` Atribut lze nastavit na plně kvalifikovaný název domény místního počítače, nikoli název localhost, který se používá ve výchozím nastavení. Tím je zajištěno lepší dodržování standardů protokolu SMTP. Výchozí hodnota je název localhost místního počítače odesílajícího požadavek. Vlastnost lze použít k získání aktuální hodnoty `clientDomain` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>  
  
 `targetName` Atribut se používá pro ověřování při použití rozšířené ochrany. Výchozí hodnota je ve formátu "SMTPSVC/\<hostitel >", kde \<hostitelský > je název hostitele poštovního serveru SMTP. Vlastnost lze použít k získání aktuální hodnoty `targetName` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>  
  
 `enableSsl` Atribut určuje, zda se pro přístup k poštovnímu serveru SMTP používá protokol SSL. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Třída podporuje jenom rozšíření služby SMTP pro zabezpečený protokol SMTP přes Transport Layer Security, jak je definované v dokumentu RFC 3207. V tomto režimu bude relace SMTP začínat nešifrovaným kanálem, a poté se na server vystaví příkaz STARTTLS, který přepne na zabezpečenou komunikaci pomocí protokolu SSL. Další informace najdete v dokumentu RFC 3207 publikovaného sdružením IETF (Internet Engineering Task Force).  
  
 Alternativním způsobem připojení je, že relace SSL se vytvoří před odesláním příkazů protokolu. Tato metoda připojení se někdy označuje jako SMTP a ve výchozím nastavení používá port 465. Tato alternativní metoda připojení používající protokol SSL se momentálně nepodporuje.  
  
 Vlastnost lze použít k získání aktuální hodnoty `enableSsl` atributu z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.  
  
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
- [Schéma nastavení sítě](index.md)
