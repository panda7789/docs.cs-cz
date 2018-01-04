---
title: "Konfigurační oddíl pro model Windows Forms"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
ms.workload: dotnet
ms.openlocfilehash: f2d83f5dcf6fa93ceba4d670470bd768a2ee1f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="22de4-102">Konfigurační oddíl pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22de4-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="22de4-103">Windows Forms – nastavení konfigurace povolit aplikaci Windows Forms k ukládání a načíst informace o nastavení vlastní aplikace, jako je například více monitorů, vysoké DPI podpory a další předdefinovaná nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="22de4-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="22de4-104">Nastavení konfigurace aplikace Windows Forms jsou uložené v souboru konfigurace aplikace `System.Windows.Forms.ApplicationConfigurationSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="22de4-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="22de4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22de4-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22de4-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22de4-106">Attributes and elements</span></span>

<span data-ttu-id="22de4-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22de4-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="22de4-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="22de4-108">Attributes</span></span>

<span data-ttu-id="22de4-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="22de4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22de4-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="22de4-110">Child elements</span></span>

<span data-ttu-id="22de4-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="22de4-111">Element</span></span>  |<span data-ttu-id="22de4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="22de4-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="22de4-113">Přidá klíč nastavení konfigurace se zadanou hodnotou</span><span class="sxs-lookup"><span data-stu-id="22de4-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="22de4-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="22de4-114">Parent elements</span></span>

<span data-ttu-id="22de4-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="22de4-115">Element</span></span>  |<span data-ttu-id="22de4-116">Popis</span><span class="sxs-lookup"><span data-stu-id="22de4-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="22de4-117">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="22de4-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="22de4-118">Kořenový element v každém konfiguračním souboru používá modul common language runtime a systém Windows Forms aplikace</span><span class="sxs-lookup"><span data-stu-id="22de4-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="22de4-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22de4-119">Remarks</span></span>

<span data-ttu-id="22de4-120">Od verze 4.7 rozhraní .NET Framework, `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje nakonfigurovat aplikace Windows Forms chcete využít výhod funkce přidané v posledních verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22de4-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="22de4-121">`<System.Windows.Forms.ApplicationConfigurationSection>` Element může obsahovat jeden nebo více podřízených [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) prvky, z nichž každý definuje konkrétní konfigurační nastavení.</span><span class="sxs-lookup"><span data-stu-id="22de4-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="22de4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="22de4-122">See also</span></span>

<span data-ttu-id="22de4-123">[Schéma konfiguračního souboru](../index.md) </span><span class="sxs-lookup"><span data-stu-id="22de4-123">[Configuration File Schema](../index.md) </span></span>  
[<span data-ttu-id="22de4-124">Podpora vysoké DPI ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22de4-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
