---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4a54df0b6301f1aae14d5561c91c6792cb0a1620
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109816"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="6a267-102">Konfigurační oddíl pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6a267-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="6a267-103">Nastavení konfigurace model Windows Forms umožňuje aplikaci model Windows Forms ukládat a načítat informace o přizpůsobených nastaveních aplikace, jako je podpora více monitorů, podpora vysokého rozlišení DPI a další předdefinovaná nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6a267-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="6a267-104">Model Windows Forms nastavení konfigurace aplikace jsou uložena v `System.Windows.Forms.ApplicationConfigurationSection` elementu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a267-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a267-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a267-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a267-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6a267-106">Attributes and elements</span></span>

<span data-ttu-id="6a267-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6a267-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a267-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="6a267-108">Attributes</span></span>

<span data-ttu-id="6a267-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="6a267-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a267-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6a267-110">Child elements</span></span>

<span data-ttu-id="6a267-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a267-111">Element</span></span>  |<span data-ttu-id="6a267-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6a267-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="6a267-113">Přidá klíč nastavení konfigurace se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="6a267-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="6a267-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6a267-114">Parent elements</span></span>

<span data-ttu-id="6a267-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a267-115">Element</span></span>  |<span data-ttu-id="6a267-116">Popis</span><span class="sxs-lookup"><span data-stu-id="6a267-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="6a267-117">Konfigurace \<</span><span class="sxs-lookup"><span data-stu-id="6a267-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="6a267-118">Kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a model Windows Forms aplikacemi</span><span class="sxs-lookup"><span data-stu-id="6a267-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="6a267-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a267-119">Remarks</span></span>

<span data-ttu-id="6a267-120">Počínaje .NET Framework 4,7 `<System.Windows.Forms.ApplicationConfigurationSection>` prvek umožňuje nakonfigurovat model Windows Forms aplikace, aby využívaly funkce přidané v posledních verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a267-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="6a267-121">Element `<System.Windows.Forms.ApplicationConfigurationSection>` může obsahovat jeden nebo více podřízených [`<add>`](windows-forms-add-configuration-element.md) prvků, z nichž každý definuje konkrétní nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6a267-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a267-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a267-122">See also</span></span>

- [<span data-ttu-id="6a267-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="6a267-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6a267-124">Podpora vysokého rozlišení DPI v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6a267-124">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
