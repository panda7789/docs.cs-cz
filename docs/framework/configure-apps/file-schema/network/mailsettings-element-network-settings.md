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
ms.openlocfilehash: b8ea08cbd76e60a3665703bc50924dd94500cd87
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659321"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="93c09-102">\<mailSettings – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="93c09-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="93c09-103">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="93c09-103">Configures mail sending options.</span></span>  

<span data-ttu-id="93c09-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="93c09-104">\<configuration></span></span>  
<span data-ttu-id="93c09-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="93c09-105">\<system.net></span></span>  
<span data-ttu-id="93c09-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="93c09-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93c09-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93c09-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93c09-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93c09-108">Attributes and Elements</span></span>  
 <span data-ttu-id="93c09-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93c09-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93c09-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="93c09-110">Attributes</span></span>  
 <span data-ttu-id="93c09-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="93c09-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93c09-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="93c09-112">Child Elements</span></span>  
  
|<span data-ttu-id="93c09-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="93c09-113">Attribute</span></span>|<span data-ttu-id="93c09-114">Popis</span><span class="sxs-lookup"><span data-stu-id="93c09-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="93c09-115">\<> elementu SMTP (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="93c09-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="93c09-116">Nakonfiguruje možnosti jednoduchého poštovního transportního protokolu.</span><span class="sxs-lookup"><span data-stu-id="93c09-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93c09-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="93c09-117">Parent Elements</span></span>  
  
|<span data-ttu-id="93c09-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="93c09-118">**Element**</span></span>|<span data-ttu-id="93c09-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="93c09-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="93c09-120">\<System .NET > – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="93c09-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="93c09-121">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="93c09-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="93c09-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="93c09-122">Example</span></span>  
 <span data-ttu-id="93c09-123">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="93c09-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93c09-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93c09-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="93c09-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="93c09-125">Network Settings Schema</span></span>](index.md)
