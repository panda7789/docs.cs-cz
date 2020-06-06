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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154813"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="bf0af-102">\<network> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="bf0af-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="bf0af-103">Nakonfiguruje možnosti sítě pro externí server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="bf0af-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="bf0af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf0af-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf0af-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bf0af-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bf0af-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bf0af-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf0af-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="bf0af-107">Attributes</span></span>  
  
|<span data-ttu-id="bf0af-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="bf0af-108">Attribute</span></span>|<span data-ttu-id="bf0af-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bf0af-109">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="bf0af-110">Určuje název domény klienta, který má být použit v počátečním požadavku protokolu SMTP pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-110">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="bf0af-111">Výchozí hodnota je název localhost místního počítače odesílajícího požadavek.</span><span class="sxs-lookup"><span data-stu-id="bf0af-111">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="bf0af-112">Určuje, zda mají být pro přístup k poštovnímu serveru SMTP pro transakce SMTP použity přihlašovací údaje výchozího uživatele.</span><span class="sxs-lookup"><span data-stu-id="bf0af-112">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="bf0af-113">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="bf0af-113">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="bf0af-114">Určuje, zda se pro přístup k poštovnímu serveru SMTP používá protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="bf0af-114">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="bf0af-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="bf0af-115">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="bf0af-116">Určuje název hostitele poštovního serveru SMTP, který se má použít pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-116">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="bf0af-117">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bf0af-117">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="bf0af-118">Určuje heslo, které se má použít pro ověřování na poštovním serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-118">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="bf0af-119">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bf0af-119">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="bf0af-120">Určuje číslo portu, který se má použít pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-120">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="bf0af-121">Výchozí hodnota je 25.</span><span class="sxs-lookup"><span data-stu-id="bf0af-121">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="bf0af-122">Určuje název poskytovatele služeb (SPN), který se má použít pro ověřování při použití rozšířené ochrany pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-122">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="bf0af-123">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bf0af-123">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="bf0af-124">Určuje uživatelské jméno, které se má použít pro ověřování na poštovním serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-124">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="bf0af-125">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bf0af-125">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf0af-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bf0af-126">Child Elements</span></span>  
 <span data-ttu-id="bf0af-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf0af-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf0af-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bf0af-128">Parent Elements</span></span>  
  
|<span data-ttu-id="bf0af-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="bf0af-129">Element</span></span>|<span data-ttu-id="bf0af-130">Description</span><span class="sxs-lookup"><span data-stu-id="bf0af-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf0af-131">\<smtp>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="bf0af-131">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="bf0af-132">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="bf0af-132">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf0af-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf0af-133">Remarks</span></span>  
 <span data-ttu-id="bf0af-134">Některé servery SMTP vyžadují, abyste se před použitím ověřili na server.</span><span class="sxs-lookup"><span data-stu-id="bf0af-134">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="bf0af-135">Pokud se chcete ověřit pomocí výchozích síťových přihlašovacích údajů na hostiteli, nastavte `defaultCredentials` atribut na `true` .</span><span class="sxs-lookup"><span data-stu-id="bf0af-135">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="bf0af-136"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `defaultCredentials` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="bf0af-136">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="bf0af-137">K ověření vašeho vlastního serveru SMTP můžete použít také základní ověřování (uživatelské jméno a heslo).</span><span class="sxs-lookup"><span data-stu-id="bf0af-137">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="bf0af-138">Chcete-li použít tuto možnost, je nutné zadat platné uživatelské jméno a heslo pro zadaný server SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-138">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf0af-139">Základní ověřování odesílá `userName` hodnoty a `password` na server nešifrovaný.</span><span class="sxs-lookup"><span data-stu-id="bf0af-139">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="bf0af-140">Kdokoli, kdo sleduje síťový provoz, může zobrazit vaše přihlašovací údaje a použít je k připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="bf0af-140">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="bf0af-141">Měli byste zvážit použití bezpečnějšího mechanismu ověřování, jako je například Kerberos nebo NT LAN Manager (NTLM). Pokud `defaultCredentials` je `true` , použije se protokol Kerberos nebo NTLM, pokud server tyto protokoly podporuje.</span><span class="sxs-lookup"><span data-stu-id="bf0af-141">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="bf0af-142">Možnosti základního ověřování a výchozích síťových přihlašovacích údajů se vzájemně vylučují. Pokud nastavíte `defaultCredentials` `true` a zadáte uživatelské jméno a heslo, použije se výchozí síťová pověření a data základního ověřování se ignorují.</span><span class="sxs-lookup"><span data-stu-id="bf0af-142">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="bf0af-143">Pro základní ověřování Pokud zadáte `userName` , měli byste taky určit, jestli se má na `password` poštovní server sami ověřit.</span><span class="sxs-lookup"><span data-stu-id="bf0af-143">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="bf0af-144"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `userName` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="bf0af-144">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="bf0af-145"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `password` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="bf0af-145">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="bf0af-146">`password`Z bezpečnostních důvodů se atribut v konfiguračních souborech obvykle nezadá.</span><span class="sxs-lookup"><span data-stu-id="bf0af-146">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="bf0af-147">`clientDomain`Atribut změní název domény klienta použitý v počátečním požadavku protokolu SMTP na server SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-147">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="bf0af-148">`clientDomain`Atribut lze nastavit na plně kvalifikovaný název domény místního počítače, nikoli název localhost, který se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="bf0af-148">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="bf0af-149">Tím je zajištěno lepší dodržování standardů protokolu SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-149">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="bf0af-150">Výchozí hodnota je název localhost místního počítače odesílajícího požadavek.</span><span class="sxs-lookup"><span data-stu-id="bf0af-150">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="bf0af-151"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `clientDomain` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="bf0af-151">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="bf0af-152">`targetName`Atribut se používá pro ověřování při použití rozšířené ochrany.</span><span class="sxs-lookup"><span data-stu-id="bf0af-152">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="bf0af-153">Výchozí hodnota je ve formátu "SMTPSVC/", \<host> kde \<host> je název hostitele poštovního serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf0af-153">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="bf0af-154"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `targetName` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="bf0af-154">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="bf0af-155">`enableSsl`Atribut určuje, zda se pro přístup k poštovnímu serveru SMTP používá protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="bf0af-155">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="bf0af-156"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>Třída podporuje jenom rozšíření služby SMTP pro zabezpečený protokol SMTP přes Transport Layer Security, jak je definované v dokumentu RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="bf0af-156">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="bf0af-157">V tomto režimu bude relace SMTP začínat nešifrovaným kanálem, a poté se na server vystaví příkaz STARTTLS, který přepne na zabezpečenou komunikaci pomocí protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="bf0af-157">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="bf0af-158">Další informace najdete v dokumentu RFC 3207 publikovaného sdružením IETF (Internet Engineering Task Force).</span><span class="sxs-lookup"><span data-stu-id="bf0af-158">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="bf0af-159">Alternativním způsobem připojení je, že relace SSL se vytvoří před odesláním příkazů protokolu.</span><span class="sxs-lookup"><span data-stu-id="bf0af-159">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="bf0af-160">Tato metoda připojení se někdy označuje jako SMTP a ve výchozím nastavení používá port 465.</span><span class="sxs-lookup"><span data-stu-id="bf0af-160">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="bf0af-161">Tato alternativní metoda připojení používající protokol SSL se momentálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="bf0af-161">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="bf0af-162"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `enableSsl` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="bf0af-162">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf0af-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf0af-163">Example</span></span>  
 <span data-ttu-id="bf0af-164">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="bf0af-164">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf0af-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf0af-165">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="bf0af-166">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="bf0af-166">Network Settings Schema</span></span>](index.md)
