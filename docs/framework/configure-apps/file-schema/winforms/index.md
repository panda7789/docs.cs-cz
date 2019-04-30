---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbb2c4157ba702182056c98c959a60569e8c3d1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786409"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="b72cd-102">Konfigurační oddíl pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b72cd-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="b72cd-103">Povolit aplikaci Windows Forms k uložení nastavení konfigurace Windows Forms a načíst informace o nastavení vlastní aplikace, jako je podpora více monitorů, podpora vysoké rozlišení DPI a další předdefinované nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b72cd-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="b72cd-104">Nastavení konfigurace aplikace Windows Forms jsou uloženy v souboru konfigurace aplikace `System.Windows.Forms.ApplicationConfigurationSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="b72cd-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="b72cd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b72cd-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b72cd-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b72cd-106">Attributes and elements</span></span>

<span data-ttu-id="b72cd-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b72cd-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b72cd-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="b72cd-108">Attributes</span></span>

<span data-ttu-id="b72cd-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="b72cd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b72cd-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b72cd-110">Child elements</span></span>

<span data-ttu-id="b72cd-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="b72cd-111">Element</span></span>  |<span data-ttu-id="b72cd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b72cd-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="b72cd-113">Přidá klíč nastavení konfigurace se zadanou hodnotou</span><span class="sxs-lookup"><span data-stu-id="b72cd-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b72cd-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="b72cd-114">Parent elements</span></span>

<span data-ttu-id="b72cd-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="b72cd-115">Element</span></span>  |<span data-ttu-id="b72cd-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b72cd-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="b72cd-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b72cd-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="b72cd-118">Kořenový element v každém konfiguračním souboru tak, že modul common language runtime a Windows Forms používané aplikace</span><span class="sxs-lookup"><span data-stu-id="b72cd-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="b72cd-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b72cd-119">Remarks</span></span>

<span data-ttu-id="b72cd-120">Od verze rozhraní .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje konfigurace aplikací Windows Forms, abyste mohli využívat funkce přidané v posledních verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b72cd-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="b72cd-121">`<System.Windows.Forms.ApplicationConfigurationSection>` Element může obsahovat jednu nebo více podřízených [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) prvky, z nichž každý definuje konkrétní nastavení.</span><span class="sxs-lookup"><span data-stu-id="b72cd-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="b72cd-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b72cd-122">See also</span></span>

- [<span data-ttu-id="b72cd-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b72cd-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b72cd-124">Podpora vysokého nastavení DPI ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b72cd-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
