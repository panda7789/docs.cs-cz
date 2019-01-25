---
title: 'Průvodce: Provádění obecných úloh pomocí inteligentních značek na Windows Forms ovládací prvky'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: b17fbaea48660a47630dd310c74be9cd3cc78609
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579313"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="159bc-102">Průvodce: Provádění obecných úloh pomocí inteligentních značek na Windows Forms ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="159bc-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="159bc-103">Jak vytvořit formuláře a ovládací prvky pro aplikace Windows Forms, existují mnoho úloh, které budete opakovaně provádět.</span><span class="sxs-lookup"><span data-stu-id="159bc-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="159bc-104">Toto jsou některé běžně prováděné úlohy, které se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="159bc-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="159bc-105">Přidání nebo odebrání kartu na <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="159bc-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="159bc-106">Ukotvení ovládacího prvku k nadřazené úloze.</span><span class="sxs-lookup"><span data-stu-id="159bc-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="159bc-107">Změna orientace <xref:System.Windows.Forms.SplitContainer> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="159bc-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="159bc-108">Mnoho ovládacích prvků pro rychlejší vývoj, nabízí inteligentní značky, které jsou kontextové nabídky, které umožňují provádět běžné úkoly, jako jsou tyto jedním gestem v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="159bc-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="159bc-109">Tyto úlohy se nazývají *smart-tag příkazy*.</span><span class="sxs-lookup"><span data-stu-id="159bc-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="159bc-110">Inteligentní značky zůstanou připojené k instanci ovládacího prvku po dobu jeho platnosti v návrháři a jsou vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="159bc-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="159bc-111">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="159bc-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="159bc-112">Vytvoření projektu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="159bc-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="159bc-113">Pomocí inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="159bc-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="159bc-114">Povolení a zakázání inteligentní značky</span><span class="sxs-lookup"><span data-stu-id="159bc-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="159bc-115">Až budete hotovi, budete mít znalosti o úloze, kterou tyto funkce důležité rozložení.</span><span class="sxs-lookup"><span data-stu-id="159bc-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="159bc-116">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="159bc-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="159bc-117">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="159bc-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="159bc-118">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="159bc-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="159bc-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="159bc-119">Creating the Project</span></span>  
 <span data-ttu-id="159bc-120">Prvním krokem je vytvoření projektu a nastavení formuláře.</span><span class="sxs-lookup"><span data-stu-id="159bc-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="159bc-121">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="159bc-121">To create the project</span></span>  
  
1.  <span data-ttu-id="159bc-122">Vytvořte projekt aplikace pro systém Windows s názvem "SmartTagsExample" (**souboru** > **nový** > **projektu**  >   **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="159bc-122">Create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="159bc-123">Vyberte formulář v nástrojích pro **Návrháře formulářů Windows**.</span><span class="sxs-lookup"><span data-stu-id="159bc-123">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="159bc-124">Pomocí inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="159bc-124">Using Smart Tags</span></span>  
 <span data-ttu-id="159bc-125">Inteligentní značky jsou vždy k dispozici na ovládací prvky, které nabízejí je v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="159bc-125">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="159bc-126">Použití inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="159bc-126">To use smart tags</span></span>  
  
1.  <span data-ttu-id="159bc-127">Přetáhněte <xref:System.Windows.Forms.TabControl> z **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="159bc-127">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="159bc-128">Všimněte si smart piktogram (![piktogram inteligentní](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), který se zobrazí na straně aplikace <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="159bc-128">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="159bc-129">Klikněte na tlačítko smart piktogram.</span><span class="sxs-lookup"><span data-stu-id="159bc-129">Click the smart-tag glyph.</span></span> <span data-ttu-id="159bc-130">V místní nabídce, která se zobrazí vedle šifra, vyberte **přidat kartu** položky.</span><span class="sxs-lookup"><span data-stu-id="159bc-130">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="159bc-131">Podívejte se, že je do nové stránky karty <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="159bc-131">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="159bc-132">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="159bc-132">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="159bc-133">Klikněte na tlačítko smart piktogram.</span><span class="sxs-lookup"><span data-stu-id="159bc-133">Click the smart-tag glyph.</span></span> <span data-ttu-id="159bc-134">V místní nabídce, která se zobrazí vedle šifra, vyberte **přidat sloupec** položky.</span><span class="sxs-lookup"><span data-stu-id="159bc-134">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="159bc-135">Podívejte se, že nový sloupec se přidá do <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="159bc-135">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="159bc-136">Přetáhněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="159bc-136">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="159bc-137">Klikněte na tlačítko smart piktogram.</span><span class="sxs-lookup"><span data-stu-id="159bc-137">Click the smart-tag glyph.</span></span> <span data-ttu-id="159bc-138">V místní nabídce, která se zobrazí vedle šifra, vyberte **orientace vodorovné příčky** položky.</span><span class="sxs-lookup"><span data-stu-id="159bc-138">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="159bc-139">Zda se zobrazila zpráva <xref:System.Windows.Forms.SplitContainer> ovládacího prvku rozdělovač je nyní orientovaný vodorovně.</span><span class="sxs-lookup"><span data-stu-id="159bc-139">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="159bc-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="159bc-140">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- [<span data-ttu-id="159bc-141">Návod: Přidání inteligentních značek ke komponentě ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="159bc-141">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](https://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
