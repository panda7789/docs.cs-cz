---
title: <mailSettings> – element (nastavení sítě)
description: <mailSettings>Prvek nastavení sítě konfiguruje možnosti odeslání pošty v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: ce7b8564e4ee5ea73d42259612c077420d36645b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504560"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="11110-103">\<mailSettings> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="11110-103">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="11110-104">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="11110-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="11110-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11110-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11110-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11110-106">Attributes and Elements</span></span>  
 <span data-ttu-id="11110-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11110-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11110-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="11110-108">Attributes</span></span>  
 <span data-ttu-id="11110-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="11110-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="11110-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11110-110">Child Elements</span></span>  
  
|<span data-ttu-id="11110-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="11110-111">Attribute</span></span>|<span data-ttu-id="11110-112">Popis</span><span class="sxs-lookup"><span data-stu-id="11110-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="11110-113">\<smtp>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="11110-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="11110-114">Nakonfiguruje možnosti jednoduchého poštovního transportního protokolu.</span><span class="sxs-lookup"><span data-stu-id="11110-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11110-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11110-115">Parent Elements</span></span>  
  
|<span data-ttu-id="11110-116">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="11110-116">**Element**</span></span>|<span data-ttu-id="11110-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="11110-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="11110-118">\<system.Net>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="11110-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="11110-119">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="11110-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="11110-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="11110-120">Example</span></span>  
 <span data-ttu-id="11110-121">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="11110-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11110-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11110-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="11110-123">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="11110-123">Network Settings Schema</span></span>](index.md)
