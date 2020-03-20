---
title: Konfigurační oddíl pro model Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151829"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="916a7-102">Konfigurační oddíl pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="916a7-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="916a7-103">Nastavení konfigurace windows forms umožňují aplikaci Windows Forms ukládat a načítat informace o přizpůsobených nastaveních aplikací, jako je podpora více monitorů, vysoká podpora DPI a další předdefinovaná nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="916a7-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="916a7-104">Nastavení konfigurace aplikace windows forms jsou uložena `System.Windows.Forms.ApplicationConfigurationSection` v prvku konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="916a7-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="916a7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="916a7-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="916a7-106">Atributy a prvky</span><span class="sxs-lookup"><span data-stu-id="916a7-106">Attributes and elements</span></span>

<span data-ttu-id="916a7-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="916a7-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="916a7-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="916a7-108">Attributes</span></span>

<span data-ttu-id="916a7-109">Žádné.</span><span class="sxs-lookup"><span data-stu-id="916a7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="916a7-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="916a7-110">Child elements</span></span>

<span data-ttu-id="916a7-111">Element</span><span class="sxs-lookup"><span data-stu-id="916a7-111">Element</span></span>  |<span data-ttu-id="916a7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="916a7-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="916a7-113">Přidá klíč nastavení konfigurace se zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="916a7-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="916a7-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="916a7-114">Parent elements</span></span>

<span data-ttu-id="916a7-115">Element</span><span class="sxs-lookup"><span data-stu-id="916a7-115">Element</span></span>  |<span data-ttu-id="916a7-116">Popis</span><span class="sxs-lookup"><span data-stu-id="916a7-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="916a7-117">\<>konfigurace</span><span class="sxs-lookup"><span data-stu-id="916a7-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="916a7-118">Kořenový prvek v každém konfiguračním souboru používaném běžným jazykem runtime a aplikacemi Windows Forms</span><span class="sxs-lookup"><span data-stu-id="916a7-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="916a7-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="916a7-119">Remarks</span></span>

<span data-ttu-id="916a7-120">Počínaje rozhraním .NET Framework 4.7 umožňuje `<System.Windows.Forms.ApplicationConfigurationSection>` tento prvek konfigurovat aplikace windows forms tak, aby využívaly funkce přidané v posledních verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="916a7-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="916a7-121">Prvek `<System.Windows.Forms.ApplicationConfigurationSection>` může obsahovat jeden [`<add>`](windows-forms-add-configuration-element.md) nebo více podřízených prvků, z nichž každý definuje konkrétní nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="916a7-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="916a7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="916a7-122">See also</span></span>

- [<span data-ttu-id="916a7-123">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="916a7-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="916a7-124">Vysoká podpora DPI ve formulářích systému Windows</span><span class="sxs-lookup"><span data-stu-id="916a7-124">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
