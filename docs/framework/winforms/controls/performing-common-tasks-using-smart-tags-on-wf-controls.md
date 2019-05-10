---
title: 'Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211420"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="245e7-102">Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="245e7-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>

<span data-ttu-id="245e7-103">Jak vytvořit formuláře a ovládací prvky pro aplikace Windows Forms, existují mnoho úloh, které budete opakovaně provádět.</span><span class="sxs-lookup"><span data-stu-id="245e7-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="245e7-104">Toto jsou některé běžně prováděné úlohy, které se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="245e7-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="245e7-105">Přidání nebo odebrání kartu na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="245e7-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="245e7-106">Ukotvení ovládacího prvku k nadřazené úloze.</span><span class="sxs-lookup"><span data-stu-id="245e7-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="245e7-107">Změna orientace <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="245e7-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="245e7-108">Mnoho ovládacích prvků pro rychlejší vývoj, nabízí inteligentní značky, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou tyto jedním gestem v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="245e7-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="245e7-109">Tyto úlohy se nazývají *smart-tag příkazy*.</span><span class="sxs-lookup"><span data-stu-id="245e7-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="245e7-110">Inteligentní značky zůstanou připojené k instanci ovládacího prvku po dobu jeho platnosti v návrháři a jsou vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="245e7-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

<span data-ttu-id="245e7-111">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="245e7-111">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="245e7-112">Vytvoření projektu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="245e7-112">Creating a Windows Forms project</span></span>

- <span data-ttu-id="245e7-113">Pomocí inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="245e7-113">Using smart tags</span></span>

- <span data-ttu-id="245e7-114">Povolení a zakázání inteligentní značky</span><span class="sxs-lookup"><span data-stu-id="245e7-114">Enabling and Disabling Smart Tags</span></span>

<span data-ttu-id="245e7-115">Až budete hotovi, budete mít znalosti o úloze, kterou tyto funkce důležité rozložení.</span><span class="sxs-lookup"><span data-stu-id="245e7-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="245e7-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="245e7-116">Create the project</span></span>

<span data-ttu-id="245e7-117">Prvním krokem je vytvoření projektu a nastavení formuláře.</span><span class="sxs-lookup"><span data-stu-id="245e7-117">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="245e7-118">V sadě Visual Studio vytvořte projekt aplikace pro systém Windows s názvem "SmartTagsExample" (**souboru** > **nový** > **projektu**  >  **Visual C#**  nebo **jazyka Visual Basic** > **klasický desktopový** > **Windows Forms Aplikace**).</span><span class="sxs-lookup"><span data-stu-id="245e7-118">In Visual Studio, create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="245e7-119">Vyberte formulář v nástrojích pro **Návrháře formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="245e7-119">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="245e7-120">Použití inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="245e7-120">Use smart tags</span></span>

<span data-ttu-id="245e7-121">Inteligentní značky jsou vždy k dispozici na ovládací prvky, které nabízejí je v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="245e7-121">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="245e7-122">Přetáhněte <xref:System.Windows.Forms.TabControl> z **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="245e7-122">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="245e7-123">Všimněte si smart piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), který se zobrazí na straně aplikace <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="245e7-123">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="245e7-124">Klikněte na tlačítko smart piktogram.</span><span class="sxs-lookup"><span data-stu-id="245e7-124">Click the smart-tag glyph.</span></span> <span data-ttu-id="245e7-125">V místní nabídce, která se zobrazí vedle šifra, vyberte **přidat kartu** položky.</span><span class="sxs-lookup"><span data-stu-id="245e7-125">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="245e7-126">Podívejte se, že je do nové stránky karty <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="245e7-126">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="245e7-127">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="245e7-127">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="245e7-128">Klikněte na tlačítko smart piktogram.</span><span class="sxs-lookup"><span data-stu-id="245e7-128">Click the smart-tag glyph.</span></span> <span data-ttu-id="245e7-129">V místní nabídce, která se zobrazí vedle šifra, vyberte **přidat sloupec** položky.</span><span class="sxs-lookup"><span data-stu-id="245e7-129">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="245e7-130">Podívejte se, že nový sloupec se přidá do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="245e7-130">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="245e7-131">Přetáhněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="245e7-131">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="245e7-132">Klikněte na tlačítko smart piktogram.</span><span class="sxs-lookup"><span data-stu-id="245e7-132">Click the smart-tag glyph.</span></span> <span data-ttu-id="245e7-133">V místní nabídce, která se zobrazí vedle šifra, vyberte **orientace vodorovné příčky** položky.</span><span class="sxs-lookup"><span data-stu-id="245e7-133">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="245e7-134">Zda se zobrazila zpráva <xref:System.Windows.Forms.SplitContainer> ovládacího prvku rozdělovač je nyní orientovaný vodorovně.</span><span class="sxs-lookup"><span data-stu-id="245e7-134">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="245e7-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="245e7-135">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- <span data-ttu-id="245e7-136">[Návod: Přidání inteligentních značek ke komponentě ve Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="245e7-136">[Walkthrough: Adding Smart Tags to a Windows Forms Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span></span>
