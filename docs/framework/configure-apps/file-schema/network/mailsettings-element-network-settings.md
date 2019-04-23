---
title: <mailSettings> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 54fb68ab0bf8aa2665d70391350c626131ccb4bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180620"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="c7673-102">\<mailSettings – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c7673-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="c7673-103">Konfiguruje možnosti pro odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="c7673-103">Configures mail sending options.</span></span>  

<span data-ttu-id="c7673-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c7673-104">\<configuration></span></span>  
<span data-ttu-id="c7673-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c7673-105">\<system.net></span></span>  
<span data-ttu-id="c7673-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="c7673-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7673-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7673-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7673-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c7673-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c7673-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c7673-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7673-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c7673-110">Attributes</span></span>  
 <span data-ttu-id="c7673-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="c7673-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c7673-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c7673-112">Child Elements</span></span>  
  
|<span data-ttu-id="c7673-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c7673-113">Attribute</span></span>|<span data-ttu-id="c7673-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c7673-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c7673-115">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c7673-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="c7673-116">Nakonfiguruje možnosti Simple Mail Transfer Protocol.</span><span class="sxs-lookup"><span data-stu-id="c7673-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7673-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c7673-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c7673-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="c7673-118">**Element**</span></span>|<span data-ttu-id="c7673-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c7673-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c7673-120">\<system.Net > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c7673-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="c7673-121">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="c7673-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7673-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7673-122">Example</span></span>  
 <span data-ttu-id="c7673-123">Následující příklad určuje příslušné parametry protokolu SMTP k odesílání e-mailů pomocí výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="c7673-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7673-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7673-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="c7673-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c7673-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
