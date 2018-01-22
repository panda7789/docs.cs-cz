---
title: "Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2fb4e8bf710e55be0a817a4154dfbce114db191
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="58d4d-102">Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58d4d-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="58d4d-103">Jak vytvořit formuláře a ovládací prvky pro aplikaci Windows Forms, existují řadu úkolů, které provedete opakovaně.</span><span class="sxs-lookup"><span data-stu-id="58d4d-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="58d4d-104">Toto jsou některé běžně prováděné úlohy, které mohou být zobrazeny:</span><span class="sxs-lookup"><span data-stu-id="58d4d-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="58d4d-105">Přidání nebo odebrání na kartě <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="58d4d-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="58d4d-106">Ukotvení nadřazenému prvku.</span><span class="sxs-lookup"><span data-stu-id="58d4d-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="58d4d-107">Změna orientace <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58d4d-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="58d4d-108">Pro rychlejší vývoj, nabízí mnoho ovládacích prvků inteligentních značek, které jsou kontextové nabídky, které vám umožní provádět běžné úkoly, jako v jednom gesto v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="58d4d-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="58d4d-109">Tyto úlohy se nazývají *technologie Smart příkazy*.</span><span class="sxs-lookup"><span data-stu-id="58d4d-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="58d4d-110">Inteligentní značky budou připojeny k instanci ovládacího prvku pro své životnosti v návrháři a jsou vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="58d4d-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="58d4d-111">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="58d4d-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="58d4d-112">Vytvoření projektu modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58d4d-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="58d4d-113">Pomocí inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="58d4d-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="58d4d-114">Povolení a zakázání inteligentní značky</span><span class="sxs-lookup"><span data-stu-id="58d4d-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="58d4d-115">Jakmile budete hotovi, budete mít představu o úloze, kterou tyto funkce důležité rozložení.</span><span class="sxs-lookup"><span data-stu-id="58d4d-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58d4d-116">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="58d4d-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="58d4d-117">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="58d4d-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="58d4d-118">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="58d4d-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="58d4d-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="58d4d-119">Creating the Project</span></span>  
 <span data-ttu-id="58d4d-120">Prvním krokem je vytvoření projektu a nastavte formulář.</span><span class="sxs-lookup"><span data-stu-id="58d4d-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="58d4d-121">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="58d4d-121">To create the project</span></span>  
  
1.  <span data-ttu-id="58d4d-122">Vytvořte projekt aplikace pro systém Windows s názvem "SmartTagsExample".</span><span class="sxs-lookup"><span data-stu-id="58d4d-122">Create a Windows-based application project called "SmartTagsExample".</span></span> <span data-ttu-id="58d4d-123">Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="58d4d-123">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="58d4d-124">Vybrat formuláře v **Návrhář formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="58d4d-124">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="58d4d-125">Pomocí inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="58d4d-125">Using Smart Tags</span></span>  
 <span data-ttu-id="58d4d-126">Inteligentní značky jsou vždy k dispozici v době návrhu na ovládací prvky, které nabízejí je.</span><span class="sxs-lookup"><span data-stu-id="58d4d-126">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="58d4d-127">Použití inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="58d4d-127">To use smart tags</span></span>  
  
1.  <span data-ttu-id="58d4d-128">Přetáhněte <xref:System.Windows.Forms.TabControl> z **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="58d4d-128">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="58d4d-129">Všimněte si glyfy čipové tag (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), zobrazí se na sebe z <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="58d4d-129">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="58d4d-130">Klikněte na tlačítko glyfy čipové tag.</span><span class="sxs-lookup"><span data-stu-id="58d4d-130">Click the smart-tag glyph.</span></span> <span data-ttu-id="58d4d-131">V místní nabídce, který se zobrazí vedle glyf, vyberte **přidat karta** položky.</span><span class="sxs-lookup"><span data-stu-id="58d4d-131">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="58d4d-132">Zkontrolujte, že nová stránka karta je přidat do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="58d4d-132">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="58d4d-133">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="58d4d-133">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="58d4d-134">Klikněte na tlačítko glyfy čipové tag.</span><span class="sxs-lookup"><span data-stu-id="58d4d-134">Click the smart-tag glyph.</span></span> <span data-ttu-id="58d4d-135">V místní nabídce, který se zobrazí vedle glyf, vyberte **přidat sloupec** položky.</span><span class="sxs-lookup"><span data-stu-id="58d4d-135">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="58d4d-136">Zkontrolujte, že nový sloupec přidán do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58d4d-136">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="58d4d-137">Přetáhněte <xref:System.Windows.Forms.SplitContainer> řídit z **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="58d4d-137">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="58d4d-138">Klikněte na tlačítko glyfy čipové tag.</span><span class="sxs-lookup"><span data-stu-id="58d4d-138">Click the smart-tag glyph.</span></span> <span data-ttu-id="58d4d-139">V místní nabídce, který se zobrazí vedle glyf, vyberte **vodorovný rozdělovač orientaci** položky.</span><span class="sxs-lookup"><span data-stu-id="58d4d-139">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="58d4d-140">Všimněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku rozdělovač je nyní zaměřené na konkrétní vodorovně.</span><span class="sxs-lookup"><span data-stu-id="58d4d-140">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d4d-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="58d4d-141">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="58d4d-142">Návod: Přidání inteligentních značek k součásti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58d4d-142">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
