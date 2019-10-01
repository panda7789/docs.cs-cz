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
ms.openlocfilehash: bac288bb28c4176e52366d0e0b7d8bc7d313cf96
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698005"
---
# <a name="network-element-network-settings"></a>@no__t – element > 0network (nastavení sítě)
Nakonfiguruje možnosti sítě pro externí server SMTP (Simple Mail Transport Protocol).  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<smtp >** ](smtp-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<network >**  
  
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
|[@no__t – element > 1smtp (nastavení sítě)](smtp-element-network-settings.md)|Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).|  
  
## <a name="remarks"></a>Poznámky  
 Některé servery SMTP vyžadují, abyste se před použitím ověřili na server. Pokud se chcete ověřit pomocí výchozích síťových přihlašovacích údajů hostitele, nastavte atribut `defaultCredentials` na hodnotu `true`. Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `defaultCredentials` z příslušných konfiguračních souborů.  
  
 K ověření vašeho vlastního serveru SMTP můžete použít také základní ověřování (uživatelské jméno a heslo). Chcete-li použít tuto možnost, je nutné zadat platné uživatelské jméno a heslo pro zadaný server SMTP.  
  
> [!NOTE]
> Základní ověřování odesílá nešifrované hodnoty `userName` a `password` na server. Kdokoli, kdo sleduje síťový provoz, může zobrazit vaše přihlašovací údaje a použít je k připojení k serveru. Měli byste zvážit použití bezpečnějšího mechanismu ověřování, jako je například Kerberos nebo NT LAN Manager (NTLM). Pokud je `defaultCredentials` `true`, bude použit protokol Kerberos nebo NTLM, pokud server tyto protokoly podporuje.  
  
 Možnosti základního ověřování a výchozích síťových přihlašovacích údajů se vzájemně vylučují. Pokud nastavíte `defaultCredentials` na `true` a zadáte uživatelské jméno a heslo, použije se výchozí síťová pověření a data základního ověřování se budou ignorovat.  
  
 Pro základní ověřování Pokud zadáte `userName`, měli byste taky zadat `password` k ověřování na poštovní server.  
  
 Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `userName` z příslušných konfiguračních souborů. Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `password` z příslušných konfiguračních souborů. Z bezpečnostních důvodů by se atribut `password` v konfiguračních souborech normálně nezadal.  
  
 Atribut `clientDomain` změní název domény klienta použitou v počátečním požadavku protokolu SMTP na server SMTP. Atribut `clientDomain` lze nastavit na plně kvalifikovaný název domény místního počítače, nikoli název localhost, který se používá ve výchozím nastavení. Tím je zajištěno lepší dodržování standardů protokolu SMTP. Výchozí hodnota je název localhost místního počítače odesílajícího požadavek. Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `clientDomain` z příslušných konfiguračních souborů.  
  
 Atribut `targetName` se používá pro ověřování při použití rozšířené ochrany. Výchozí hodnota je ve formátu "SMTPSVC/\<host >", kde \<Host > je název hostitele poštovního serveru SMTP. Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `targetName` z příslušných konfiguračních souborů.  
  
 Atribut `enableSsl` určuje, zda se k přístupu k poštovnímu serveru SMTP používá protokol SSL. Třída <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> podporuje jenom rozšíření služby SMTP pro zabezpečený protokol SMTP přes Transport Layer Security, jak je definované v dokumentu RFC 3207. V tomto režimu bude relace SMTP začínat nešifrovaným kanálem, a poté se na server vystaví příkaz STARTTLS, který přepne na zabezpečenou komunikaci pomocí protokolu SSL. Další informace najdete v dokumentu RFC 3207 publikovaného sdružením IETF (Internet Engineering Task Force).  
  
 Alternativním způsobem připojení je, že relace SSL se vytvoří před odesláním příkazů protokolu. Tato metoda připojení se někdy označuje jako SMTP a ve výchozím nastavení používá port 465. Tato alternativní metoda připojení používající protokol SSL se momentálně nepodporuje.  
  
 Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `enableSsl` z příslušných konfiguračních souborů.  
  
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
