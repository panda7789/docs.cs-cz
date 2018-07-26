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
manager: markl
ms.openlocfilehash: a9afd992a12392ae0ad1c27eea305cb7e367686d
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874413"
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="e2cfb-102">&lt;mailSettings&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e2cfb-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="e2cfb-103">Konfiguruje možnosti pro odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="e2cfb-103">Configures mail sending options.</span></span>  

<span data-ttu-id="e2cfb-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e2cfb-104">\<configuration></span></span>  
<span data-ttu-id="e2cfb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e2cfb-105">\<system.net></span></span>  
<span data-ttu-id="e2cfb-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="e2cfb-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2cfb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2cfb-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2cfb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e2cfb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2cfb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e2cfb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2cfb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e2cfb-110">Attributes</span></span>  
 <span data-ttu-id="e2cfb-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="e2cfb-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2cfb-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e2cfb-112">Child Elements</span></span>  
  
|<span data-ttu-id="e2cfb-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e2cfb-113">Attribute</span></span>|<span data-ttu-id="e2cfb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e2cfb-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e2cfb-115">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e2cfb-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="e2cfb-116">Nakonfiguruje možnosti Simple Mail Transfer Protocol.</span><span class="sxs-lookup"><span data-stu-id="e2cfb-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2cfb-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e2cfb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e2cfb-118">**– Element**</span><span class="sxs-lookup"><span data-stu-id="e2cfb-118">**Element**</span></span>|<span data-ttu-id="e2cfb-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e2cfb-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e2cfb-120">\<system.Net > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e2cfb-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="e2cfb-121">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="e2cfb-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e2cfb-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2cfb-122">Example</span></span>  
 <span data-ttu-id="e2cfb-123">Následující příklad určuje příslušné parametry protokolu SMTP k odesílání e-mailů pomocí výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="e2cfb-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2cfb-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2cfb-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="e2cfb-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e2cfb-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
