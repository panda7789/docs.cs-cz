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
ms.openlocfilehash: e23b9e1fdf8a348d0d38575db8112b37c8dd9b69
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50048759"
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="89ced-102">&lt;mailSettings&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="89ced-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="89ced-103">Konfiguruje možnosti pro odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="89ced-103">Configures mail sending options.</span></span>  

<span data-ttu-id="89ced-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="89ced-104">\<configuration></span></span>  
<span data-ttu-id="89ced-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="89ced-105">\<system.net></span></span>  
<span data-ttu-id="89ced-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="89ced-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ced-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89ced-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89ced-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="89ced-108">Attributes and Elements</span></span>  
 <span data-ttu-id="89ced-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="89ced-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89ced-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="89ced-110">Attributes</span></span>  
 <span data-ttu-id="89ced-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="89ced-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="89ced-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="89ced-112">Child Elements</span></span>  
  
|<span data-ttu-id="89ced-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="89ced-113">Attribute</span></span>|<span data-ttu-id="89ced-114">Popis</span><span class="sxs-lookup"><span data-stu-id="89ced-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="89ced-115">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="89ced-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="89ced-116">Nakonfiguruje možnosti Simple Mail Transfer Protocol.</span><span class="sxs-lookup"><span data-stu-id="89ced-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89ced-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="89ced-117">Parent Elements</span></span>  
  
|<span data-ttu-id="89ced-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="89ced-118">**Element**</span></span>|<span data-ttu-id="89ced-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="89ced-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="89ced-120">\<system.Net > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="89ced-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="89ced-121">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="89ced-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89ced-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="89ced-122">Example</span></span>  
 <span data-ttu-id="89ced-123">Následující příklad určuje příslušné parametry protokolu SMTP k odesílání e-mailů pomocí výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="89ced-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89ced-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="89ced-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="89ced-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="89ced-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
