---
title: "&lt;mailSettings –&gt; – Element (nastavení sítě)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a42b10574a1f44d310f86fe3fa99490f2f1981c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="28268-102">&lt;mailSettings –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="28268-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="28268-103">Nakonfiguruje možnosti odesílání e-mailu.</span><span class="sxs-lookup"><span data-stu-id="28268-103">Configures mail sending options.</span></span>  

<span data-ttu-id="28268-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="28268-104">\<configuration></span></span>  
<span data-ttu-id="28268-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="28268-105">\<system.net></span></span>  
<span data-ttu-id="28268-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="28268-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28268-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28268-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28268-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="28268-108">Attributes and Elements</span></span>  
 <span data-ttu-id="28268-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="28268-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28268-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="28268-110">Attributes</span></span>  
 <span data-ttu-id="28268-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="28268-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="28268-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="28268-112">Child Elements</span></span>  
  
|<span data-ttu-id="28268-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="28268-113">Attribute</span></span>|<span data-ttu-id="28268-114">Popis</span><span class="sxs-lookup"><span data-stu-id="28268-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="28268-115">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="28268-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="28268-116">Nakonfiguruje možnosti protokolu přenosu e-mailu.</span><span class="sxs-lookup"><span data-stu-id="28268-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28268-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="28268-117">Parent Elements</span></span>  
  
|<span data-ttu-id="28268-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="28268-118">**Element**</span></span>|<span data-ttu-id="28268-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="28268-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="28268-120">\<system.Net > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="28268-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="28268-121">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="28268-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28268-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="28268-122">Example</span></span>  
 <span data-ttu-id="28268-123">Následující příklad určuje vhodné parametry SMTP pro odeslání e-mailu pomocí výchozích pověření sítě.</span><span class="sxs-lookup"><span data-stu-id="28268-123">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28268-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="28268-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="28268-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="28268-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
