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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089235"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="90745-102">\<mailSettings> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="90745-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="90745-103">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="90745-103">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="90745-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90745-104">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90745-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90745-105">Attributes and Elements</span></span>  
 <span data-ttu-id="90745-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="90745-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90745-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="90745-107">Attributes</span></span>  
 <span data-ttu-id="90745-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="90745-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90745-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90745-109">Child Elements</span></span>  
  
|<span data-ttu-id="90745-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="90745-110">Attribute</span></span>|<span data-ttu-id="90745-111">Popis</span><span class="sxs-lookup"><span data-stu-id="90745-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="90745-112">\<smtp>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="90745-112">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="90745-113">Nakonfiguruje možnosti jednoduchého poštovního transportního protokolu.</span><span class="sxs-lookup"><span data-stu-id="90745-113">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90745-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90745-114">Parent Elements</span></span>  
  
|<span data-ttu-id="90745-115">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="90745-115">**Element**</span></span>|<span data-ttu-id="90745-116">**Popis**</span><span class="sxs-lookup"><span data-stu-id="90745-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="90745-117">\<system.Net>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="90745-117">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="90745-118">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="90745-118">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="90745-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="90745-119">Example</span></span>  
 <span data-ttu-id="90745-120">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="90745-120">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90745-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="90745-121">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="90745-122">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="90745-122">Network Settings Schema</span></span>](index.md)
