---
title: <network> – element (nastavení sítě)
description: <network>Prvek nastavení sítě konfiguruje možnosti sítě pro externí možnosti serveru SMTP v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: 36857e63871b4672df349934594f0887a042609e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504547"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="3caca-103">\<network> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3caca-103">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="3caca-104">Nakonfiguruje možnosti sítě pro externí server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="3caca-104">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="3caca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3caca-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3caca-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3caca-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3caca-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3caca-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3caca-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="3caca-108">Attributes</span></span>  
  
|<span data-ttu-id="3caca-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="3caca-109">Attribute</span></span>|<span data-ttu-id="3caca-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3caca-110">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="3caca-111">Určuje název domény klienta, který má být použit v počátečním požadavku protokolu SMTP pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-111">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="3caca-112">Výchozí hodnota je název localhost místního počítače odesílajícího požadavek.</span><span class="sxs-lookup"><span data-stu-id="3caca-112">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="3caca-113">Určuje, zda mají být pro přístup k poštovnímu serveru SMTP pro transakce SMTP použity přihlašovací údaje výchozího uživatele.</span><span class="sxs-lookup"><span data-stu-id="3caca-113">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="3caca-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="3caca-114">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="3caca-115">Určuje, zda se pro přístup k poštovnímu serveru SMTP používá protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="3caca-115">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="3caca-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="3caca-116">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="3caca-117">Určuje název hostitele poštovního serveru SMTP, který se má použít pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-117">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="3caca-118">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3caca-118">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="3caca-119">Určuje heslo, které se má použít pro ověřování na poštovním serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-119">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="3caca-120">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3caca-120">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="3caca-121">Určuje číslo portu, který se má použít pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-121">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="3caca-122">Výchozí hodnota je 25.</span><span class="sxs-lookup"><span data-stu-id="3caca-122">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="3caca-123">Určuje název poskytovatele služeb (SPN), který se má použít pro ověřování při použití rozšířené ochrany pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-123">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="3caca-124">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3caca-124">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="3caca-125">Určuje uživatelské jméno, které se má použít pro ověřování na poštovním serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-125">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="3caca-126">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3caca-126">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3caca-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3caca-127">Child Elements</span></span>  
 <span data-ttu-id="3caca-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="3caca-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3caca-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3caca-129">Parent Elements</span></span>  
  
|<span data-ttu-id="3caca-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="3caca-130">Element</span></span>|<span data-ttu-id="3caca-131">Description</span><span class="sxs-lookup"><span data-stu-id="3caca-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3caca-132">\<smtp>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3caca-132">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="3caca-133">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="3caca-133">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3caca-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3caca-134">Remarks</span></span>  
 <span data-ttu-id="3caca-135">Některé servery SMTP vyžadují, abyste se před použitím ověřili na server.</span><span class="sxs-lookup"><span data-stu-id="3caca-135">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="3caca-136">Pokud se chcete ověřit pomocí výchozích síťových přihlašovacích údajů na hostiteli, nastavte `defaultCredentials` atribut na `true` .</span><span class="sxs-lookup"><span data-stu-id="3caca-136">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="3caca-137"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `defaultCredentials` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="3caca-137">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3caca-138">K ověření vašeho vlastního serveru SMTP můžete použít také základní ověřování (uživatelské jméno a heslo).</span><span class="sxs-lookup"><span data-stu-id="3caca-138">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="3caca-139">Chcete-li použít tuto možnost, je nutné zadat platné uživatelské jméno a heslo pro zadaný server SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-139">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3caca-140">Základní ověřování odesílá `userName` hodnoty a `password` na server nešifrovaný.</span><span class="sxs-lookup"><span data-stu-id="3caca-140">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="3caca-141">Kdokoli, kdo sleduje síťový provoz, může zobrazit vaše přihlašovací údaje a použít je k připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="3caca-141">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="3caca-142">Měli byste zvážit použití bezpečnějšího mechanismu ověřování, jako je například Kerberos nebo NT LAN Manager (NTLM). Pokud `defaultCredentials` je `true` , použije se protokol Kerberos nebo NTLM, pokud server tyto protokoly podporuje.</span><span class="sxs-lookup"><span data-stu-id="3caca-142">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="3caca-143">Možnosti základního ověřování a výchozích síťových přihlašovacích údajů se vzájemně vylučují. Pokud nastavíte `defaultCredentials` `true` a zadáte uživatelské jméno a heslo, použije se výchozí síťová pověření a data základního ověřování se ignorují.</span><span class="sxs-lookup"><span data-stu-id="3caca-143">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="3caca-144">Pro základní ověřování Pokud zadáte `userName` , měli byste taky určit, jestli se má na `password` poštovní server sami ověřit.</span><span class="sxs-lookup"><span data-stu-id="3caca-144">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="3caca-145"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `userName` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="3caca-145">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="3caca-146"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `password` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="3caca-146">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="3caca-147">`password`Z bezpečnostních důvodů se atribut v konfiguračních souborech obvykle nezadá.</span><span class="sxs-lookup"><span data-stu-id="3caca-147">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="3caca-148">`clientDomain`Atribut změní název domény klienta použitý v počátečním požadavku protokolu SMTP na server SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-148">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="3caca-149">`clientDomain`Atribut lze nastavit na plně kvalifikovaný název domény místního počítače, nikoli název localhost, který se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3caca-149">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="3caca-150">Tím je zajištěno lepší dodržování standardů protokolu SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-150">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="3caca-151">Výchozí hodnota je název localhost místního počítače odesílajícího požadavek.</span><span class="sxs-lookup"><span data-stu-id="3caca-151">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="3caca-152"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `clientDomain` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="3caca-152">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3caca-153">`targetName`Atribut se používá pro ověřování při použití rozšířené ochrany.</span><span class="sxs-lookup"><span data-stu-id="3caca-153">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="3caca-154">Výchozí hodnota je ve formátu "SMTPSVC/", \<host> kde \<host> je název hostitele poštovního serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="3caca-154">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="3caca-155"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `targetName` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="3caca-155">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3caca-156">`enableSsl`Atribut určuje, zda se pro přístup k poštovnímu serveru SMTP používá protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="3caca-156">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="3caca-157"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>Třída podporuje jenom rozšíření služby SMTP pro zabezpečený protokol SMTP přes Transport Layer Security, jak je definované v dokumentu RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="3caca-157">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="3caca-158">V tomto režimu bude relace SMTP začínat nešifrovaným kanálem, a poté se na server vystaví příkaz STARTTLS, který přepne na zabezpečenou komunikaci pomocí protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="3caca-158">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="3caca-159">Další informace najdete v dokumentu RFC 3207 publikovaného sdružením IETF (Internet Engineering Task Force).</span><span class="sxs-lookup"><span data-stu-id="3caca-159">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="3caca-160">Alternativním způsobem připojení je, že relace SSL se vytvoří před odesláním příkazů protokolu.</span><span class="sxs-lookup"><span data-stu-id="3caca-160">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="3caca-161">Tato metoda připojení se někdy označuje jako SMTP a ve výchozím nastavení používá port 465.</span><span class="sxs-lookup"><span data-stu-id="3caca-161">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="3caca-162">Tato alternativní metoda připojení používající protokol SSL se momentálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="3caca-162">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="3caca-163"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>Vlastnost lze použít k získání aktuální hodnoty `enableSsl` atributu z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="3caca-163">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3caca-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="3caca-164">Example</span></span>  
 <span data-ttu-id="3caca-165">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="3caca-165">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3caca-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3caca-166">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="3caca-167">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3caca-167">Network Settings Schema</span></span>](index.md)
