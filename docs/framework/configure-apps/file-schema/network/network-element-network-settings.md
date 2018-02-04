---
title: "&lt;sítě&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 913765a4d8ac12d25dff446439f6a7510e6067ae
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="ltnetworkgt-element-network-settings"></a>&lt;sítě&gt; – Element (nastavení sítě)
Nakonfiguruje možnosti sítě pro externí server přenosu protokolu SMTP (Simple Mail).  
  
 \<Konfigurace >  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<sítě >  
  
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
|`clientDomain`|Určuje název domény klienta pro použití v počáteční žádosti protokolu SMTP pro připojení k poštovnímu serveru SMTP. Výchozí hodnota je localhost název místního počítače odesílání požadavku.|  
|`defaultCredentials`|Určuje, zda by měl používat výchozí uživatelská pověření pro přístup k poštovnímu serveru SMTP pro transakce SMTP. Výchozí hodnota je `false`.|  
|`enableSsl`|Určuje, jestli je pro přístup k serveru SMTP e-mailu používat protokol SSL. Výchozí hodnota je `false`.|  
|`host`|Určuje název hostitele poštovního serveru SMTP pro transakce SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`password`|Určuje heslo používané při ověřování k poštovnímu serveru SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`port`|Udává číslo portu pro připojení k poštovnímu serveru SMTP. Výchozí hodnota je 25.|  
|`targetName`|Určuje název zprostředkovatele služby (SPN) pro ověřování pomocí při použití Rozšířená ochrana pro transakce SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
|`userName`|Určuje uživatelské jméno, které používají k ověřování pro poštovní server SMTP. Tento atribut nemá žádnou výchozí hodnotu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<SMTP > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Nakonfiguruje možnosti odesílání e-mailu přenosu protokolu SMTP (Simple Mail).|  
  
## <a name="remarks"></a>Poznámky  
 Některé servery SMTP vyžadují ověření sami k serveru před použitím. Pokud chcete ověřit sami pomocí výchozích pověření sítě na hostiteli, nastavte `defaultCredentials` atribut `true`. <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `defaultCredentials` atribut z příslušných konfiguračních souborů.  
  
 Můžete také použít základní ověřování (uživatelské jméno a heslo) k ověření se k serveru SMTP. Chcete-li použít tuto možnost, musíte zadat platné uživatelské jméno a heslo pro zadaný server SMTP.  
  
> [!NOTE]
>  Odešle základní ověřování `userName` a `password` hodnoty k serveru bez šifrování. Každý, kdo monitorování síťového provozu můžete zobrazit vaše přihlašovací údaje a použít je k připojení k serveru. Měli byste zvážit použití bezpečnější mechanismus ověřování, jako je například ověřování protokolu Kerberos nebo NT LAN Manager (NTLM). Pokud `defaultCredentials` je `true`, Kerberos nebo NTLM bude použit, pokud server podporuje tyto protokoly.  
  
 Základní ověřování a výchozí síťové přihlašovací údaje možnosti se vzájemně vylučují. Pokud nastavíte `defaultCredentials` k `true` a zadejte uživatelské jméno a heslo, se používá výchozí pověření sítě a data základní ověřování je ignorována.  
  
 Pro základní ověřování, pokud zadáte `userName`, musíte také zadat `password` ověřování sami, abyste je poštovní server.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `userName` atribut z příslušných konfiguračních souborů. <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `password` atribut z příslušných konfiguračních souborů. A `password` by za normálních okolností je třeba zadat atribut v konfiguračních souborech z bezpečnostních důvodů.  
  
 `clientDomain` Název domény klienta, který je použitý v počáteční žádosti protokolu SMTP na SMTP server, změní se atribut. `clientDomain` Atribut lze nastavit do domény plně kvalifikovaný název místního počítače, nikoli název místního hostitele, který se používá ve výchozím nastavení. To poskytuje větší dodržování standardů protokolu SMTP. Výchozí hodnota je localhost název místního počítače odesílání požadavku. <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `clientDomain` atribut z příslušných konfiguračních souborů.  
  
 `targetName` Atribut se používá k ověřování při použití rozšířené ochrany. Výchozí hodnota je ve formátu "SMTPSVC /\<hostitele >" kde \<hostitele > je název hostitele serveru SMTP, e-mailu. <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `targetName` atribut z příslušných konfiguračních souborů.  
  
 `enableSsl` Atribut určuje, jestli je pro přístup k serveru SMTP e-mailu používat protokol SSL. <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Třída podporuje pouze rozšíření pro službu SMTP pro zabezpečené SMTP přes Transport Layer Security jak jsou definovány v dokumentu RFC 3207. V tomto režimu SMTP relace začíná v nezašifrované kanály a potom příkaz STARTTLS vydává klienta k serveru a přepněte do zabezpečené komunikace pomocí protokolu SSL. Najdete v dokumentu RFC 3207 publikovaná pomocí Engineering Task Force IETF (Internet) Další informace.  
  
 Metodu alternativní připojení je, kde je relace SSL navázat předem před libovolný protokol pro příkazy jsou odeslána. Tato metoda připojení se někdy označuje jako SMTPS a ve výchozím nastavení používá port 465. Tato metoda alternativní připojení pomocí protokolu SSL není aktuálně podporován.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `enableSsl` atribut z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje vhodné parametry SMTP pro odeslání e-mailu pomocí výchozích pověření sítě.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
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
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
