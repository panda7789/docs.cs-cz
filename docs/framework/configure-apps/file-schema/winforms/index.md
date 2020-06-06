---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151829"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="a59b8-102">Konfigurační oddíl pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a59b8-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="a59b8-103">Nastavení konfigurace model Windows Forms umožňuje aplikaci model Windows Forms ukládat a načítat informace o přizpůsobených nastaveních aplikace, jako je podpora více monitorů, podpora vysokého rozlišení DPI a další předdefinovaná nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a59b8-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="a59b8-104">Model Windows Forms nastavení konfigurace aplikace jsou uložena v elementu konfiguračního souboru aplikace `System.Windows.Forms.ApplicationConfigurationSection` .</span><span class="sxs-lookup"><span data-stu-id="a59b8-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="a59b8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a59b8-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a59b8-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a59b8-106">Attributes and elements</span></span>

<span data-ttu-id="a59b8-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a59b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a59b8-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a59b8-108">Attributes</span></span>

<span data-ttu-id="a59b8-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="a59b8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a59b8-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a59b8-110">Child elements</span></span>

<span data-ttu-id="a59b8-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="a59b8-111">Element</span></span>  |<span data-ttu-id="a59b8-112">Description</span><span class="sxs-lookup"><span data-stu-id="a59b8-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="a59b8-113">Přidá klíč nastavení konfigurace se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="a59b8-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="a59b8-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="a59b8-114">Parent elements</span></span>

<span data-ttu-id="a59b8-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="a59b8-115">Element</span></span>  |<span data-ttu-id="a59b8-116">Description</span><span class="sxs-lookup"><span data-stu-id="a59b8-116">Description</span></span> |
---------|---------|
[\<configuration>](../configuration-element.md) | <span data-ttu-id="a59b8-117">Kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a model Windows Forms aplikacemi</span><span class="sxs-lookup"><span data-stu-id="a59b8-117">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="a59b8-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a59b8-118">Remarks</span></span>

<span data-ttu-id="a59b8-119">Počínaje .NET Framework 4,7 `<System.Windows.Forms.ApplicationConfigurationSection>` element umožňuje nakonfigurovat model Windows Forms aplikace, aby využívaly výhody funkcí přidaných v posledních verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a59b8-119">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="a59b8-120">`<System.Windows.Forms.ApplicationConfigurationSection>`Element může obsahovat jeden nebo více podřízených [`<add>`](windows-forms-add-configuration-element.md) elementů, z nichž každý definuje konkrétní nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a59b8-120">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="a59b8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a59b8-121">See also</span></span>

- [<span data-ttu-id="a59b8-122">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a59b8-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a59b8-123">Podpora vysokého rozlišení DPI v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a59b8-123">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
