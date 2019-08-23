---
title: 'Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964293"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="37b58-102">Postupy: Úprava vstupu klávesnice do standardního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="37b58-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="37b58-103">Model Windows Forms poskytuje možnost využívat a upravovat vstup z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="37b58-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="37b58-104">Spotřebovávání klíče odkazuje na zpracování klíče v rámci metody nebo obslužné rutiny události, aby jiné metody a události v nižší části fronty zpráv neobdržely hodnotu klíče.</span><span class="sxs-lookup"><span data-stu-id="37b58-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="37b58-105">Změna klíče odkazuje na úpravu hodnoty klíče tak, aby metody a obslužné rutiny událostí dále v dolní části fronty zpráv přijímaly jinou hodnotu klíče.</span><span class="sxs-lookup"><span data-stu-id="37b58-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="37b58-106">V tomto tématu se dozvíte, jak tyto úlohy provést.</span><span class="sxs-lookup"><span data-stu-id="37b58-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="37b58-107">Využití klíče</span><span class="sxs-lookup"><span data-stu-id="37b58-107">To consume a key</span></span>  
  
- <span data-ttu-id="37b58-108">V obslužné rutině <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyPressEventArgs> události nastavte vlastnost třídy na `true`. <xref:System.Windows.Forms.Control.KeyPress></span><span class="sxs-lookup"><span data-stu-id="37b58-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="37b58-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="37b58-109">-or-</span></span>  
  
     <span data-ttu-id="37b58-110">V obslužné rutině <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyEventArgs> události nastavte vlastnost třídy na `true`. <xref:System.Windows.Forms.Control.KeyDown></span><span class="sxs-lookup"><span data-stu-id="37b58-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="37b58-111">Nastavení vlastnosti v obslužné rutině události nebrání <xref:System.Windows.Forms.Control.KeyUp> vyvolání událostí aproaktuálníklávesovouzkratku.<xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Control.KeyDown> <xref:System.Windows.Forms.KeyEventArgs.Handled%2A></span><span class="sxs-lookup"><span data-stu-id="37b58-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="37b58-112">Pro tento účel použijte vlastnost.<xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A></span><span class="sxs-lookup"><span data-stu-id="37b58-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="37b58-113">Následující `switch` příklad je výpis z příkazu, který <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> prochází vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> přijímanou <xref:System.Windows.Forms.Control.KeyPress> obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="37b58-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="37b58-114">Tento kód využívá klíče "A" a "a".</span><span class="sxs-lookup"><span data-stu-id="37b58-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="37b58-115">Postup úpravy standardního znakového klíče</span><span class="sxs-lookup"><span data-stu-id="37b58-115">To modify a standard character key</span></span>  
  
- <span data-ttu-id="37b58-116">V obslužné rutině <xref:System.Windows.Forms.KeyPressEventArgs> <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> <xref:System.Windows.Forms.Control.KeyPress> události nastavte vlastnost třídy na hodnotu nového znakového klíče.</span><span class="sxs-lookup"><span data-stu-id="37b58-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="37b58-117">Následující příklad je výňatek z `switch` příkazu, který upravuje b ' a ' a ' b ' na ' a '.</span><span class="sxs-lookup"><span data-stu-id="37b58-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="37b58-118">Všimněte si, <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> že vlastnost <xref:System.Windows.Forms.KeyPressEventArgs> parametru je nastavena na `false`hodnotu, takže nová hodnota klíče je šířena do jiných metod a událostí ve frontě zpráv.</span><span class="sxs-lookup"><span data-stu-id="37b58-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="37b58-119">Postup úpravy neznakového klíče</span><span class="sxs-lookup"><span data-stu-id="37b58-119">To modify a noncharacter key</span></span>  
  
- <span data-ttu-id="37b58-120">Přepište <xref:System.Windows.Forms.Message.WParam%2A> <xref:System.Windows.Forms.Message> <xref:System.Windows.Forms.Keys> metodu, která zpracovává zprávy systému Windows, detekuje zprávu WM_KEYDOWN nebo WM_SYSKEYDOWN a nastavte vlastnost parametru na hodnotu, která představuje nový neznakový klíč. <xref:System.Windows.Forms.Control></span><span class="sxs-lookup"><span data-stu-id="37b58-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="37b58-121">Následující příklad kódu ukazuje, jak přepsat <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metodu ovládacího prvku pro detekci klíčů F1 po F9 a změnit všechny klávesy F3 stisknutím klávesy F1.</span><span class="sxs-lookup"><span data-stu-id="37b58-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="37b58-122">Další informace o <xref:System.Windows.Forms.Control> metodách, které lze přepsat pro zachycení zpráv klávesnice, najdete [v tématu vstup uživatele v aplikaci model Windows Forms](user-input-in-a-windows-forms-application.md) a [Jak funguje vstup z klávesnice](how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="37b58-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="37b58-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="37b58-123">Example</span></span>  
 <span data-ttu-id="37b58-124">Následující příklad kódu je úplná aplikace pro příklady kódu v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="37b58-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="37b58-125">Aplikace používá vlastní ovládací prvek odvozený od <xref:System.Windows.Forms.TextBox> třídy pro využívání a úpravy vstupu z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="37b58-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37b58-126">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="37b58-126">Compiling the Code</span></span>  
 <span data-ttu-id="37b58-127">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="37b58-127">This example requires:</span></span>  
  
- <span data-ttu-id="37b58-128">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="37b58-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b58-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37b58-129">See also</span></span>

- [<span data-ttu-id="37b58-130">Vstup z klávesnice v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37b58-130">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="37b58-131">Uživatelský vstup v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37b58-131">User Input in a Windows Forms Application</span></span>](user-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="37b58-132">Jak funguje vstup z klávesnice</span><span class="sxs-lookup"><span data-stu-id="37b58-132">How Keyboard Input Works</span></span>](how-keyboard-input-works.md)
