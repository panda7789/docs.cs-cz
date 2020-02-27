---
title: Provádění běžných úloh pomocí akcí návrháře u ovládacích prvků
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634881"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a><span data-ttu-id="5a647-102">Návod: provádění běžných úloh pomocí akcí návrháře</span><span class="sxs-lookup"><span data-stu-id="5a647-102">Walkthrough: Perform common tasks using designer actions</span></span>

<span data-ttu-id="5a647-103">Když vytváříte formuláře a ovládací prvky pro model Windows Forms aplikaci, budete opakovaně provádět mnoho úkolů.</span><span class="sxs-lookup"><span data-stu-id="5a647-103">As you construct forms and controls for your Windows Forms application, there are many tasks you'll perform repeatedly.</span></span> <span data-ttu-id="5a647-104">V následujícím seznamu jsou uvedeny některé běžné úkoly, které se budou provádět v rámci:</span><span class="sxs-lookup"><span data-stu-id="5a647-104">The following list shows some of the commonly performed tasks you'll come across:</span></span>

- <span data-ttu-id="5a647-105">Přidání nebo odebrání karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="5a647-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>
- <span data-ttu-id="5a647-106">Ukotvení ovládacího prvku k nadřazenému objektu.</span><span class="sxs-lookup"><span data-stu-id="5a647-106">Docking a control to its parent.</span></span>
- <span data-ttu-id="5a647-107">Změna orientace ovládacího prvku <xref:System.Windows.Forms.SplitContainer>.</span><span class="sxs-lookup"><span data-stu-id="5a647-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="5a647-108">K urychlení vývoje nabízí mnoho ovládacích prvků i akce návrháře, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou například v jednom gestu v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="5a647-108">To speed development, many controls offer designer actions, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="5a647-109">Tyto úlohy se nazývají *operace návrháře akcí*.</span><span class="sxs-lookup"><span data-stu-id="5a647-109">These tasks are called *designer actions verbs*.</span></span>

<span data-ttu-id="5a647-110">Akce návrháře zůstávají v Návrháři připojeny k instanci ovládacího prvku a jsou vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5a647-110">Designer actions remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="5a647-111">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="5a647-111">Create the project</span></span>

<span data-ttu-id="5a647-112">Prvním krokem je vytvoření projektu a nastavení formuláře.</span><span class="sxs-lookup"><span data-stu-id="5a647-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="5a647-113">V aplikaci Visual Studio vytvořte projekt aplikace založený na systému Windows s názvem **DesignerActionsExample**.</span><span class="sxs-lookup"><span data-stu-id="5a647-113">In Visual Studio, create a Windows-based application project called **DesignerActionsExample**.</span></span>

2. <span data-ttu-id="5a647-114">Vyberte formulář v **Návrhář formulářů**.</span><span class="sxs-lookup"><span data-stu-id="5a647-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-designer-actions"></a><span data-ttu-id="5a647-115">Použití akcí návrháře</span><span class="sxs-lookup"><span data-stu-id="5a647-115">Use designer actions</span></span>

<span data-ttu-id="5a647-116">Akce návrháře jsou vždy k dispozici v době návrhu u ovládacích prvků, které je nabízejí.</span><span class="sxs-lookup"><span data-stu-id="5a647-116">Designer actions are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="5a647-117">Přetáhněte <xref:System.Windows.Forms.TabControl> ze **sady nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="5a647-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="5a647-118">Všimněte si, že glyf akcí návrháře (![malé černé šipky](./media/designer-actions-glyph.gif)), který se zobrazí na straně <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="5a647-118">Note the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="5a647-119">Klikněte na piktogram akcí návrháře.</span><span class="sxs-lookup"><span data-stu-id="5a647-119">Click the designer actions glyph.</span></span> <span data-ttu-id="5a647-120">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat kartu** .</span><span class="sxs-lookup"><span data-stu-id="5a647-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="5a647-121">Všimněte si, že se do <xref:System.Windows.Forms.TabControl>přidá nová stránka karty.</span><span class="sxs-lookup"><span data-stu-id="5a647-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="5a647-122">Přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="5a647-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="5a647-123">Klikněte na piktogram akcí návrháře.</span><span class="sxs-lookup"><span data-stu-id="5a647-123">Click the designer actions glyph.</span></span> <span data-ttu-id="5a647-124">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat sloupec** .</span><span class="sxs-lookup"><span data-stu-id="5a647-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="5a647-125">Všimněte si, že je do ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> přidán nový sloupec.</span><span class="sxs-lookup"><span data-stu-id="5a647-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="5a647-126">Přetáhněte ovládací prvek <xref:System.Windows.Forms.SplitContainer> z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="5a647-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="5a647-127">Klikněte na piktogram akcí návrháře.</span><span class="sxs-lookup"><span data-stu-id="5a647-127">Click the designer actions glyph.</span></span> <span data-ttu-id="5a647-128">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **orientace vodorovné příčky** .</span><span class="sxs-lookup"><span data-stu-id="5a647-128">In the shortcut menu that appears next to the glyph, select the **Horizontal Splitter Orientation** item.</span></span> <span data-ttu-id="5a647-129">Všimněte si, že příčka ovládacího prvku <xref:System.Windows.Forms.SplitContainer> je nyní orientována vodorovně.</span><span class="sxs-lookup"><span data-stu-id="5a647-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a647-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a647-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
