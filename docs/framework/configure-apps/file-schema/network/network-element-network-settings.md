---
title: '&lt;síť&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: 242ee42ded339b349cb9e4eb93750b9f5db29b51
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135229"
---
# <a name="ltnetworkgt-element-network-settings"></a><span data-ttu-id="2ed02-102">&lt;síť&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2ed02-102">&lt;network&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2ed02-103">Konfiguruje možnosti sítě pro externí server Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="2ed02-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="2ed02-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2ed02-104">\<configuration></span></span>  
<span data-ttu-id="2ed02-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2ed02-105">\<system.net></span></span>  
<span data-ttu-id="2ed02-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="2ed02-106">\<mailSettings></span></span>  
<span data-ttu-id="2ed02-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="2ed02-107">\<smtp></span></span>  
<span data-ttu-id="2ed02-108">\<sítě ></span><span class="sxs-lookup"><span data-stu-id="2ed02-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed02-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ed02-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ed02-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ed02-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2ed02-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ed02-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ed02-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ed02-112">Attributes</span></span>  
  
|<span data-ttu-id="2ed02-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ed02-113">Attribute</span></span>|<span data-ttu-id="2ed02-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2ed02-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="2ed02-115">Určuje název domény klienta pro použití v prvotní žádosti protokolu SMTP pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="2ed02-116">Výchozí hodnota je localhost název místního počítače, které odesílá požadavek.</span><span class="sxs-lookup"><span data-stu-id="2ed02-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="2ed02-117">Určuje, zda by měl použít výchozí pověření uživatele pro přístup k poštovnímu serveru SMTP pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="2ed02-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="2ed02-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="2ed02-119">Určuje, zda se používá protokol SSL pro přístup k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="2ed02-120">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="2ed02-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="2ed02-121">Určuje název hostitele poštovního serveru SMTP pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="2ed02-122">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2ed02-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="2ed02-123">Určuje heslo pro účely ověření k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="2ed02-124">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2ed02-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="2ed02-125">Udává číslo portu pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="2ed02-126">Výchozí hodnota je 25.</span><span class="sxs-lookup"><span data-stu-id="2ed02-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="2ed02-127">Určuje název zprostředkovatele služby (SPN) pro účely ověření při používání rozšířené ochrany pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="2ed02-128">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2ed02-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="2ed02-129">Určuje uživatelské jméno pro účely ověření k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="2ed02-130">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2ed02-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ed02-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ed02-131">Child Elements</span></span>  
 <span data-ttu-id="2ed02-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ed02-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ed02-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ed02-133">Parent Elements</span></span>  
  
|<span data-ttu-id="2ed02-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ed02-134">Element</span></span>|<span data-ttu-id="2ed02-135">Popis</span><span class="sxs-lookup"><span data-stu-id="2ed02-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ed02-136">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2ed02-136">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="2ed02-137">Konfiguruje možnosti pro odesílání pošty Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="2ed02-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ed02-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ed02-138">Remarks</span></span>  
 <span data-ttu-id="2ed02-139">Některé servery SMTP vyžadují ověření sami na server před použitím.</span><span class="sxs-lookup"><span data-stu-id="2ed02-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="2ed02-140">Pokud chcete provést ověření pomocí výchozích síťových přihlašovacích údajů na hostiteli, nastavte `defaultCredentials` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="2ed02-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="2ed02-141"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `defaultCredentials` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="2ed02-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2ed02-142">Můžete také použít základní ověřování (uživatelské jméno a heslo) k sami ověření serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="2ed02-143">Pokud chcete použít tuto možnost, musíte zadat platné uživatelské jméno a heslo pro zadaný server SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ed02-144">Základní ověřování odešle `userName` a `password` hodnoty server v nezašifrované.</span><span class="sxs-lookup"><span data-stu-id="2ed02-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="2ed02-145">Kdokoli na nich monitorování síťového provozu můžete zobrazit svoje přihlašovací údaje a použít pro připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="2ed02-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="2ed02-146">Měli byste zvážit použití bezpečnější mechanismu ověřování, jako je protokol Kerberos nebo NT LAN Manager (NTLM). Pokud `defaultCredentials` je `true`, Kerberos nebo NTLM bude použit, pokud server podporuje tyto protokoly.</span><span class="sxs-lookup"><span data-stu-id="2ed02-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="2ed02-147">Základní ověřování a výchozí síťové přihlašovací údaje možnosti se vzájemně vylučují. Pokud nastavíte `defaultCredentials` k `true` a zadejte uživatelské jméno a heslo, se používá výchozí pověření sítě a data základního ověřování, je ignorován.</span><span class="sxs-lookup"><span data-stu-id="2ed02-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="2ed02-148">Pro základní ověřování, pokud zadáte `userName`, byste zadat také `password` ověřování sami poštovním serveru.</span><span class="sxs-lookup"><span data-stu-id="2ed02-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="2ed02-149"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `userName` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="2ed02-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="2ed02-150"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `password` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="2ed02-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="2ed02-151">A `password` by normálně je třeba zadat atribut v konfiguračních souborech z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="2ed02-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="2ed02-152">`clientDomain` Atribut změní název domény klienta použitý v původní žádost protokolu SMTP na serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="2ed02-153">`clientDomain` Atribut může být nastaven plně kvalifikovaný název domény z místního počítače, nikoli název localhost, který se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2ed02-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="2ed02-154">To poskytuje větší dodržování standardů protokol SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="2ed02-155">Výchozí hodnota je localhost název místního počítače, které odesílá požadavek.</span><span class="sxs-lookup"><span data-stu-id="2ed02-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="2ed02-156"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `clientDomain` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="2ed02-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2ed02-157">`targetName` Atribut se používá k ověřování při použití rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="2ed02-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="2ed02-158">Výchozí hodnota je ve formátu "SMTPSVC /\<hostitele >" kde \<hostitele > je název hostitele serveru SMTP, e-mailu.</span><span class="sxs-lookup"><span data-stu-id="2ed02-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="2ed02-159"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `targetName` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="2ed02-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2ed02-160">`enableSsl` Atribut určuje, zda se používá protokol SSL pro přístup k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ed02-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="2ed02-161"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Třídy podporuje pouze rozšíření služby SMTP pro zabezpečený protokol SMTP přes Transport Layer Security jak jsou definovány v dokumentu RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="2ed02-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="2ed02-162">V tomto režimu SMTP relace začíná nešifrovaný kanál a pak je vydán příkaz STARTTLS klienta k serveru a přepnout na zabezpečenou komunikaci pomocí protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="2ed02-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="2ed02-163">Najdete v dokumentu RFC 3207 publikovaná pomocí Engineering Task Force IETF (Internet) pro další informace.</span><span class="sxs-lookup"><span data-stu-id="2ed02-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="2ed02-164">Metodu připojení je, kde relace SSL pokládáme stav, ještě před zahájením před libovolného protokolu pro odeslání příkazy.</span><span class="sxs-lookup"><span data-stu-id="2ed02-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="2ed02-165">Tato metoda připojení se někdy označuje jako SMTPS a ve výchozím nastavení používá port 465.</span><span class="sxs-lookup"><span data-stu-id="2ed02-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="2ed02-166">Tato metoda připojení pomocí protokolu SSL se momentálně nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="2ed02-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="2ed02-167"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty `enableSsl` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="2ed02-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ed02-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ed02-168">Example</span></span>  
 <span data-ttu-id="2ed02-169">Následující příklad určuje příslušné parametry protokolu SMTP k odesílání e-mailů pomocí výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="2ed02-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ed02-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ed02-170">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [<span data-ttu-id="2ed02-171">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2ed02-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
