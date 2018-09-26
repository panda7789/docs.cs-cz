---
title: '&lt;mailSettings&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f3a706edaeba551139368568a7467e0cdab3524c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171605"
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="c2804-102">&lt;mailSettings&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2804-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c2804-103">Konfiguruje možnosti pro odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="c2804-103">Configures mail sending options.</span></span>  

<span data-ttu-id="c2804-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c2804-104">\<configuration></span></span>  
<span data-ttu-id="c2804-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c2804-105">\<system.net></span></span>  
<span data-ttu-id="c2804-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="c2804-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2804-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2804-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2804-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2804-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c2804-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2804-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2804-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2804-110">Attributes</span></span>  
 <span data-ttu-id="c2804-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2804-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c2804-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c2804-112">Child Elements</span></span>  
  
|<span data-ttu-id="c2804-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c2804-113">Attribute</span></span>|<span data-ttu-id="c2804-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c2804-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c2804-115">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2804-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="c2804-116">Nakonfiguruje možnosti Simple Mail Transfer Protocol.</span><span class="sxs-lookup"><span data-stu-id="c2804-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2804-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c2804-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c2804-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="c2804-118">**Element**</span></span>|<span data-ttu-id="c2804-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c2804-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c2804-120">\<system.Net > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2804-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="c2804-121">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="c2804-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c2804-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2804-122">Example</span></span>  
 <span data-ttu-id="c2804-123">Následující příklad určuje příslušné parametry protokolu SMTP k odesílání e-mailů pomocí výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="c2804-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
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
  
## <a name="see-also"></a><span data-ttu-id="c2804-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2804-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="c2804-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c2804-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
