---
title: 'Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015767"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="beea6-102">Návod: Provádění běžných úloh pomocí inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="beea6-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="beea6-103">Když vytváříte formuláře a ovládací prvky pro vaši model Windows Forms aplikaci, budete opakovaně provádět spoustu úloh.</span><span class="sxs-lookup"><span data-stu-id="beea6-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="beea6-104">Toto jsou některé běžně prováděné úkoly, které se vám budou nacházet:</span><span class="sxs-lookup"><span data-stu-id="beea6-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="beea6-105">Přidání nebo odebrání karty na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="beea6-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="beea6-106">Ukotvení ovládacího prvku k nadřazenému objektu.</span><span class="sxs-lookup"><span data-stu-id="beea6-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="beea6-107">Změna orientace <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="beea6-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="beea6-108">K urychlení vývoje nabízí mnoho ovládacích prvků inteligentní značky, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou v jednom gestu v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="beea6-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="beea6-109">Tyto úlohy se nazývají *operace inteligentních značek*.</span><span class="sxs-lookup"><span data-stu-id="beea6-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="beea6-110">Inteligentní značky zůstávají připojeny k instanci ovládacího prvku pro svou životnost v návrháři a jsou vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="beea6-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="beea6-111">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="beea6-111">Create the project</span></span>

<span data-ttu-id="beea6-112">Prvním krokem je vytvoření projektu a nastavení formuláře.</span><span class="sxs-lookup"><span data-stu-id="beea6-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="beea6-113">V aplikaci Visual Studio vytvořte projekt aplikace založený na systému Windows s názvem **SmartTagsExample**.</span><span class="sxs-lookup"><span data-stu-id="beea6-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="beea6-114">Vyberte formulář v **Návrhář formulářů**.</span><span class="sxs-lookup"><span data-stu-id="beea6-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="beea6-115">Použití inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="beea6-115">Use smart tags</span></span>

<span data-ttu-id="beea6-116">Inteligentní značky jsou vždy k dispozici v době návrhu u ovládacích prvků, které je nabízejí.</span><span class="sxs-lookup"><span data-stu-id="beea6-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="beea6-117">Přetáhněte z panelu nástrojů do formuláře. <xref:System.Windows.Forms.TabControl></span><span class="sxs-lookup"><span data-stu-id="beea6-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="beea6-118">Poznamenejte si glyf inteligentních značek![(glyf](./media/vs-winformsmttagglyph.gif)inteligentních značek), který se zobrazí <xref:System.Windows.Forms.TabControl>na straně.</span><span class="sxs-lookup"><span data-stu-id="beea6-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="beea6-119">Klikněte na glyf inteligentních značek.</span><span class="sxs-lookup"><span data-stu-id="beea6-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="beea6-120">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat kartu** .</span><span class="sxs-lookup"><span data-stu-id="beea6-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="beea6-121">Všimněte si, že je do okna <xref:System.Windows.Forms.TabControl>přidána nová stránka karty.</span><span class="sxs-lookup"><span data-stu-id="beea6-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="beea6-122">Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="beea6-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="beea6-123">Klikněte na glyf inteligentních značek.</span><span class="sxs-lookup"><span data-stu-id="beea6-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="beea6-124">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **Přidat sloupec** .</span><span class="sxs-lookup"><span data-stu-id="beea6-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="beea6-125">Všimněte si, že je do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku přidán nový sloupec.</span><span class="sxs-lookup"><span data-stu-id="beea6-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="beea6-126">Přetáhněte ovládací prvek z **panelu nástrojů** do formuláře. <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="beea6-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="beea6-127">Klikněte na glyf inteligentních značek.</span><span class="sxs-lookup"><span data-stu-id="beea6-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="beea6-128">V místní nabídce, která se zobrazí vedle glyfu, vyberte položku **orientace vodorovné příčky** .</span><span class="sxs-lookup"><span data-stu-id="beea6-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="beea6-129">Všimněte si <xref:System.Windows.Forms.SplitContainer> , že příčka ovládacího prvku je nyní orientována vodorovně.</span><span class="sxs-lookup"><span data-stu-id="beea6-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="beea6-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="beea6-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
