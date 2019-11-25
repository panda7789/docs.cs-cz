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
ms.openlocfilehash: 4e8bf23ce39edadf80f019315c690b597b3d7361
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089235"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="7867d-102">\<element > mailSettings (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7867d-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="7867d-103">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="7867d-103">Configures mail sending options.</span></span>  

<span data-ttu-id="7867d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7867d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7867d-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7867d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="7867d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<mailSettings >**</span><span class="sxs-lookup"><span data-stu-id="7867d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7867d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7867d-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7867d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7867d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7867d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7867d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7867d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7867d-110">Attributes</span></span>  
 <span data-ttu-id="7867d-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="7867d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7867d-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7867d-112">Child Elements</span></span>  
  
|<span data-ttu-id="7867d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7867d-113">Attribute</span></span>|<span data-ttu-id="7867d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7867d-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="7867d-115">\<element > SMTP (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7867d-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="7867d-116">Nakonfiguruje možnosti jednoduchého poštovního transportního protokolu.</span><span class="sxs-lookup"><span data-stu-id="7867d-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7867d-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7867d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7867d-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="7867d-118">**Element**</span></span>|<span data-ttu-id="7867d-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="7867d-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7867d-120">\<– element > systému .NET (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7867d-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="7867d-121">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="7867d-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7867d-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="7867d-122">Example</span></span>  
 <span data-ttu-id="7867d-123">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="7867d-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7867d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7867d-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="7867d-125">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="7867d-125">Network Settings Schema</span></span>](index.md)
