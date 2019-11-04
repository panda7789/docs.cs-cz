---
title: 'Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459571"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="c3297-102">Návod: provádění běžných úloh pomocí inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="c3297-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="c3297-103">Když vytváříte formuláře a ovládací prvky pro vaši model Windows Forms aplikaci, budete opakovaně provádět spoustu úloh.</span><span class="sxs-lookup"><span data-stu-id="c3297-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="c3297-104">Toto jsou některé běžně prováděné úkoly, které se vám budou nacházet:</span><span class="sxs-lookup"><span data-stu-id="c3297-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="c3297-105">Přidání nebo odebrání karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="c3297-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="c3297-106">Ukotvení ovládacího prvku k nadřazenému objektu.</span><span class="sxs-lookup"><span data-stu-id="c3297-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="c3297-107">Změna orientace ovládacího prvku <xref:System.Windows.Forms.SplitContainer>.</span><span class="sxs-lookup"><span data-stu-id="c3297-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="c3297-108">K urychlení vývoje nabízí mnoho ovládacích prvků inteligentní značky, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou v jednom gestu v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="c3297-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="c3297-109">Tyto úlohy se nazývají *operace inteligentních značek*.</span><span class="sxs-lookup"><span data-stu-id="c3297-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="c3297-110">Inteligentní značky zůstávají připojeny k instanci ovládacího prvku pro svou životnost v návrháři a jsou vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c3297-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c3297-111">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c3297-111">Create the project</span></span>

<span data-ttu-id="c3297-112">Prvním krokem je vytvoření projektu a nastavení formuláře.</span><span class="sxs-lookup"><span data-stu-id="c3297-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="c3297-113">V aplikaci Visual Studio vytvořte projekt aplikace založený na systému Windows s názvem **SmartTagsExample**.</span><span class="sxs-lookup"><span data-stu-id="c3297-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="c3297-114">Vyberte formulář v **Návrhář formulářů**.</span><span class="sxs-lookup"><span data-stu-id="c3297-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="c3297-115">Použití inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="c3297-115">Use smart tags</span></span>

<span data-ttu-id="c3297-116">Inteligentní značky jsou vždy k dispozici v době návrhu u ovládacích prvků, které je nabízejí.</span><span class="sxs-lookup"><span data-stu-id="c3297-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="c3297-117">Přetáhněte <xref:System.Windows.Forms.TabControl> ze **sady nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c3297-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="c3297-118">Poznamenejte si glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif)), který se zobrazí na straně <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="c3297-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="c3297-119">Klikněte na glyf inteligentních značek.</span><span class="sxs-lookup"><span data-stu-id="c3297-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="c3297-120">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat kartu** .</span><span class="sxs-lookup"><span data-stu-id="c3297-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="c3297-121">Všimněte si, že se do <xref:System.Windows.Forms.TabControl>přidá nová stránka karty.</span><span class="sxs-lookup"><span data-stu-id="c3297-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="c3297-122">Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c3297-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="c3297-123">Klikněte na glyf inteligentních značek.</span><span class="sxs-lookup"><span data-stu-id="c3297-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="c3297-124">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat sloupec** .</span><span class="sxs-lookup"><span data-stu-id="c3297-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="c3297-125">Všimněte si, že je do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> přidán nový sloupec.</span><span class="sxs-lookup"><span data-stu-id="c3297-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="c3297-126">Přetáhněte ovládací prvek <xref:System.Windows.Forms.SplitContainer> z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c3297-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="c3297-127">Klikněte na glyf inteligentních značek.</span><span class="sxs-lookup"><span data-stu-id="c3297-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="c3297-128">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **orientace vodorovné příčky** .</span><span class="sxs-lookup"><span data-stu-id="c3297-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="c3297-129">Všimněte si, že příčka ovládacího prvku <xref:System.Windows.Forms.SplitContainer> je nyní orientována vodorovně.</span><span class="sxs-lookup"><span data-stu-id="c3297-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3297-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3297-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
