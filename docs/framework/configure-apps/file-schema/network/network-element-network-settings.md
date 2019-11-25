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
ms.openlocfilehash: f7b73a725cd406df9ce41e2c4522850ce974022f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089221"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="c4721-102">\<– element > sítě (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c4721-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="c4721-103">Nakonfiguruje možnosti sítě pro externí server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="c4721-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

<span data-ttu-id="c4721-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c4721-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4721-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c4721-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="c4721-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c4721-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="c4721-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<smtp >** ](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c4721-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="c4721-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<network >**</span><span class="sxs-lookup"><span data-stu-id="c4721-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c4721-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4721-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4721-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c4721-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c4721-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4721-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4721-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c4721-112">Attributes</span></span>  
  
|<span data-ttu-id="c4721-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c4721-113">Attribute</span></span>|<span data-ttu-id="c4721-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c4721-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="c4721-115">Určuje název domény klienta, který má být použit v počátečním požadavku protokolu SMTP pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="c4721-116">Výchozí hodnota je název localhost místního počítače odesílajícího požadavek.</span><span class="sxs-lookup"><span data-stu-id="c4721-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="c4721-117">Určuje, zda mají být pro přístup k poštovnímu serveru SMTP pro transakce SMTP použity přihlašovací údaje výchozího uživatele.</span><span class="sxs-lookup"><span data-stu-id="c4721-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="c4721-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c4721-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="c4721-119">Určuje, zda se pro přístup k poštovnímu serveru SMTP používá protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="c4721-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="c4721-120">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c4721-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="c4721-121">Určuje název hostitele poštovního serveru SMTP, který se má použít pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="c4721-122">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4721-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="c4721-123">Určuje heslo, které se má použít pro ověřování na poštovním serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="c4721-124">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4721-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="c4721-125">Určuje číslo portu, který se má použít pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="c4721-126">Výchozí hodnota je 25.</span><span class="sxs-lookup"><span data-stu-id="c4721-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="c4721-127">Určuje název poskytovatele služeb (SPN), který se má použít pro ověřování při použití rozšířené ochrany pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="c4721-128">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4721-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="c4721-129">Určuje uživatelské jméno, které se má použít pro ověřování na poštovním serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="c4721-130">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c4721-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4721-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c4721-131">Child Elements</span></span>  
 <span data-ttu-id="c4721-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="c4721-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4721-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c4721-133">Parent Elements</span></span>  
  
|<span data-ttu-id="c4721-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4721-134">Element</span></span>|<span data-ttu-id="c4721-135">Popis</span><span class="sxs-lookup"><span data-stu-id="c4721-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4721-136">\<element > SMTP (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c4721-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="c4721-137">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="c4721-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4721-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4721-138">Remarks</span></span>  
 <span data-ttu-id="c4721-139">Některé servery SMTP vyžadují, abyste se před použitím ověřili na server.</span><span class="sxs-lookup"><span data-stu-id="c4721-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="c4721-140">Pokud se chcete ověřit pomocí výchozích síťových přihlašovacích údajů na hostiteli, nastavte atribut `defaultCredentials` na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="c4721-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="c4721-141">Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `defaultCredentials` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c4721-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c4721-142">K ověření vašeho vlastního serveru SMTP můžete použít také základní ověřování (uživatelské jméno a heslo).</span><span class="sxs-lookup"><span data-stu-id="c4721-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="c4721-143">Chcete-li použít tuto možnost, je nutné zadat platné uživatelské jméno a heslo pro zadaný server SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4721-144">Základní ověřování odesílá `userName` a `password` hodnoty do serveru bez šifrování.</span><span class="sxs-lookup"><span data-stu-id="c4721-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="c4721-145">Kdokoli, kdo sleduje síťový provoz, může zobrazit vaše přihlašovací údaje a použít je k připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="c4721-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="c4721-146">Měli byste zvážit použití bezpečnějšího mechanismu ověřování, jako je například Kerberos nebo NT LAN Manager (NTLM). Pokud je `defaultCredentials` `true`, bude použit protokol Kerberos nebo NTLM, pokud server tyto protokoly podporuje.</span><span class="sxs-lookup"><span data-stu-id="c4721-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="c4721-147">Možnosti základního ověřování a výchozích síťových přihlašovacích údajů se vzájemně vylučují. Pokud nastavíte `defaultCredentials` na `true` a zadáte uživatelské jméno a heslo, použije se výchozí síťová pověření a data základního ověřování se budou ignorovat.</span><span class="sxs-lookup"><span data-stu-id="c4721-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="c4721-148">Pokud zadáte `userName`, měli byste pro základní ověřování zadat také `password` k ověřování na poštovním serveru.</span><span class="sxs-lookup"><span data-stu-id="c4721-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="c4721-149">Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `userName` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c4721-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="c4721-150">Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `password` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c4721-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="c4721-151">Z bezpečnostních důvodů by se atribut `password` v konfiguračních souborech normálně nezadal.</span><span class="sxs-lookup"><span data-stu-id="c4721-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="c4721-152">Atribut `clientDomain` změní název domény klienta použitý v počátečním požadavku protokolu SMTP na server SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="c4721-153">Atribut `clientDomain` lze nastavit na plně kvalifikovaný název domény místního počítače, nikoli název localhost, který se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c4721-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="c4721-154">Tím je zajištěno lepší dodržování standardů protokolu SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="c4721-155">Výchozí hodnota je název localhost místního počítače odesílajícího požadavek.</span><span class="sxs-lookup"><span data-stu-id="c4721-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="c4721-156">Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `clientDomain` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c4721-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c4721-157">Atribut `targetName` se používá pro ověřování při použití rozšířené ochrany.</span><span class="sxs-lookup"><span data-stu-id="c4721-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="c4721-158">Výchozí hodnota je ve formátu "SMTPSVC/\<Host >", kde \<hostitel > je název hostitele poštovního serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="c4721-159">Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `targetName` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c4721-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c4721-160">Atribut `enableSsl` určuje, zda se protokol SSL používá pro přístup k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="c4721-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="c4721-161">Třída <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> podporuje pouze rozšíření služby SMTP pro zabezpečený protokol SMTP přes Transport Layer Security, jak je definováno v dokumentu RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="c4721-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="c4721-162">V tomto režimu bude relace SMTP začínat nešifrovaným kanálem, a poté se na server vystaví příkaz STARTTLS, který přepne na zabezpečenou komunikaci pomocí protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="c4721-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="c4721-163">Další informace najdete v dokumentu RFC 3207 publikovaného sdružením IETF (Internet Engineering Task Force).</span><span class="sxs-lookup"><span data-stu-id="c4721-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="c4721-164">Alternativním způsobem připojení je, že relace SSL se vytvoří před odesláním příkazů protokolu.</span><span class="sxs-lookup"><span data-stu-id="c4721-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="c4721-165">Tato metoda připojení se někdy označuje jako SMTP a ve výchozím nastavení používá port 465.</span><span class="sxs-lookup"><span data-stu-id="c4721-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="c4721-166">Tato alternativní metoda připojení používající protokol SSL se momentálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c4721-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="c4721-167">Vlastnost <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu `enableSsl` z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="c4721-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4721-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4721-168">Example</span></span>  
 <span data-ttu-id="c4721-169">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="c4721-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4721-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4721-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="c4721-171">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c4721-171">Network Settings Schema</span></span>](index.md)
