---
title: "&lt;sítě&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d3e99a10403a735383ee5e1a78c1f85ac7fd8281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetworkgt-element-network-settings"></a><span data-ttu-id="51326-102">&lt;sítě&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="51326-102">&lt;network&gt; Element (Network Settings)</span></span>
<span data-ttu-id="51326-103">Nakonfiguruje možnosti sítě pro externí server přenosu protokolu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="51326-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="51326-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="51326-104">\<configuration></span></span>  
<span data-ttu-id="51326-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="51326-105">\<system.net></span></span>  
<span data-ttu-id="51326-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="51326-106">\<mailSettings></span></span>  
<span data-ttu-id="51326-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="51326-107">\<smtp></span></span>  
<span data-ttu-id="51326-108">\<sítě ></span><span class="sxs-lookup"><span data-stu-id="51326-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51326-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51326-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51326-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="51326-110">Attributes and Elements</span></span>  
 <span data-ttu-id="51326-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="51326-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51326-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="51326-112">Attributes</span></span>  
  
|<span data-ttu-id="51326-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="51326-113">Attribute</span></span>|<span data-ttu-id="51326-114">Popis</span><span class="sxs-lookup"><span data-stu-id="51326-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="51326-115">Určuje název domény klienta pro použití v počáteční žádosti protokolu SMTP pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="51326-116">Výchozí hodnota je localhost název místního počítače odesílání požadavku.</span><span class="sxs-lookup"><span data-stu-id="51326-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="51326-117">Určuje, zda by měl používat výchozí uživatelská pověření pro přístup k poštovnímu serveru SMTP pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="51326-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="51326-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="51326-119">Určuje, jestli je pro přístup k serveru SMTP e-mailu používat protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="51326-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="51326-120">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="51326-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="51326-121">Určuje název hostitele poštovního serveru SMTP pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="51326-122">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="51326-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="51326-123">Určuje heslo používané při ověřování k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="51326-124">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="51326-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="51326-125">Udává číslo portu pro připojení k poštovnímu serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="51326-126">Výchozí hodnota je 25.</span><span class="sxs-lookup"><span data-stu-id="51326-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="51326-127">Určuje název zprostředkovatele služby (SPN) pro ověřování pomocí při použití Rozšířená ochrana pro transakce SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="51326-128">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="51326-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="51326-129">Určuje uživatelské jméno, které používají k ověřování pro poštovní server SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="51326-130">Tento atribut nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="51326-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51326-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="51326-131">Child Elements</span></span>  
 <span data-ttu-id="51326-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="51326-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51326-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="51326-133">Parent Elements</span></span>  
  
|<span data-ttu-id="51326-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="51326-134">Element</span></span>|<span data-ttu-id="51326-135">Popis</span><span class="sxs-lookup"><span data-stu-id="51326-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51326-136">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="51326-136">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="51326-137">Nakonfiguruje možnosti odesílání e-mailu přenosu protokolu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="51326-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51326-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51326-138">Remarks</span></span>  
 <span data-ttu-id="51326-139">Některé servery SMTP vyžadují ověření sami k serveru před použitím.</span><span class="sxs-lookup"><span data-stu-id="51326-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="51326-140">Pokud chcete ověřit sami pomocí výchozích pověření sítě na hostiteli, nastavte `defaultCredentials` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="51326-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="51326-141"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `defaultCredentials` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="51326-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="51326-142">Můžete také použít základní ověřování (uživatelské jméno a heslo) k ověření se k serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="51326-143">Chcete-li použít tuto možnost, musíte zadat platné uživatelské jméno a heslo pro zadaný server SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51326-144">Odešle základní ověřování `userName` a `password` hodnoty k serveru bez šifrování.</span><span class="sxs-lookup"><span data-stu-id="51326-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="51326-145">Každý, kdo monitorování síťového provozu můžete zobrazit vaše přihlašovací údaje a použít je k připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="51326-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="51326-146">Měli byste zvážit použití bezpečnější mechanismus ověřování, jako je například ověřování protokolu Kerberos nebo NT LAN Manager (NTLM). Pokud `defaultCredentials` je `true`, Kerberos nebo NTLM bude použit, pokud server podporuje tyto protokoly.</span><span class="sxs-lookup"><span data-stu-id="51326-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="51326-147">Základní ověřování a výchozí síťové přihlašovací údaje možnosti se vzájemně vylučují. Pokud nastavíte `defaultCredentials` k `true` a zadejte uživatelské jméno a heslo, se používá výchozí pověření sítě a data základní ověřování je ignorována.</span><span class="sxs-lookup"><span data-stu-id="51326-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="51326-148">Pro základní ověřování, pokud zadáte `userName`, musíte také zadat `password` ověřování sami, abyste je poštovní server.</span><span class="sxs-lookup"><span data-stu-id="51326-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="51326-149"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `userName` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="51326-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="51326-150"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `password` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="51326-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="51326-151">A `password` by za normálních okolností je třeba zadat atribut v konfiguračních souborech z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="51326-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="51326-152">`clientDomain` Název domény klienta, který je použitý v počáteční žádosti protokolu SMTP na SMTP server, změní se atribut.</span><span class="sxs-lookup"><span data-stu-id="51326-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="51326-153">`clientDomain` Atribut lze nastavit do domény plně kvalifikovaný název místního počítače, nikoli název místního hostitele, který se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="51326-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="51326-154">To poskytuje větší dodržování standardů protokolu SMTP.</span><span class="sxs-lookup"><span data-stu-id="51326-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="51326-155">Výchozí hodnota je localhost název místního počítače odesílání požadavku.</span><span class="sxs-lookup"><span data-stu-id="51326-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="51326-156"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `clientDomain` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="51326-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="51326-157">`targetName` Atribut se používá k ověřování při použití rozšířené ochrany.</span><span class="sxs-lookup"><span data-stu-id="51326-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="51326-158">Výchozí hodnota je ve formátu "SMTPSVC /\<hostitele >" kde \<hostitele > je název hostitele serveru SMTP, e-mailu.</span><span class="sxs-lookup"><span data-stu-id="51326-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="51326-159"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `targetName` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="51326-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="51326-160">`enableSsl` Atribut určuje, jestli je pro přístup k serveru SMTP e-mailu používat protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="51326-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="51326-161"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> Třída podporuje pouze rozšíření pro službu SMTP pro zabezpečené SMTP přes Transport Layer Security jak jsou definovány v dokumentu RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="51326-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="51326-162">V tomto režimu SMTP relace začíná v nezašifrované kanály a potom příkaz STARTTLS vydává klienta k serveru a přepněte do zabezpečené komunikace pomocí protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="51326-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="51326-163">Najdete v dokumentu RFC 3207 publikovaná pomocí Engineering Task Force IETF (Internet) Další informace.</span><span class="sxs-lookup"><span data-stu-id="51326-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="51326-164">Metodu alternativní připojení je, kde je relace SSL navázat předem před libovolný protokol pro příkazy jsou odeslána.</span><span class="sxs-lookup"><span data-stu-id="51326-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="51326-165">Tato metoda připojení se někdy označuje jako SMTPS a ve výchozím nastavení používá port 465.</span><span class="sxs-lookup"><span data-stu-id="51326-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="51326-166">Tato metoda alternativní připojení pomocí protokolu SSL není aktuálně podporován.</span><span class="sxs-lookup"><span data-stu-id="51326-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="51326-167"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota `enableSsl` atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="51326-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51326-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="51326-168">Example</span></span>  
 <span data-ttu-id="51326-169">Následující příklad určuje vhodné parametry SMTP pro odeslání e-mailu pomocí výchozích pověření sítě.</span><span class="sxs-lookup"><span data-stu-id="51326-169">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51326-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="51326-170">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [<span data-ttu-id="51326-171">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="51326-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
