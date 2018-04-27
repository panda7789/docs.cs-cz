---
title: 'Postupy: Klonování tiskárny'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ffb9f5ab8e7b768d888f5f2800fae668e47bfc3
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="b8bf3-102">Postupy: Klonování tiskárny</span><span class="sxs-lookup"><span data-stu-id="b8bf3-102">How to: Clone a Printer</span></span>
<span data-ttu-id="b8bf3-103">Většina podniků v určitém okamžiku koupit více tiskáren stejného modelu.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="b8bf3-104">Obvykle to jsou nainstalovány s nastavením konfigurace prakticky identické.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="b8bf3-105">Instalace tiskárny může být časově náročná a chyba náchylné k chybám.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="b8bf3-106"><xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Obor názvů a <xref:System.Printing.PrintServer.InstallPrintQueue%2A> třídu, která se zveřejňují pomocí rozhraní Microsoft .NET Framework umožňuje okamžitě nainstalovat libovolný počet dalších tiskové fronty, které jsou klonovat z existující tiskovou frontu.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8bf3-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8bf3-107">Example</span></span>  
 <span data-ttu-id="b8bf3-108">V následujícím příkladu je druhý tiskové fronty klonovat z existující tiskovou frontu.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="b8bf3-109">Druhá se liší od prvního pouze v jeho název, umístění, port a sdílený stav.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="b8bf3-110">Hlavní kroky tohoto postupu jsou následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-110">The major steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="b8bf3-111">Vytvoření <xref:System.Printing.PrintQueue> objekt pro existující tiskárny, který se bude klonovat.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2.  <span data-ttu-id="b8bf3-112">Vytvoření <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> z <xref:System.Printing.PrintQueue>.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="b8bf3-113"><xref:System.Collections.DictionaryEntry.Value%2A> Vlastnost každé položky tohoto slovníku je objekt jeden z typů, které jsou odvozené z <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="b8bf3-114">Existují dva způsoby, jak nastavit hodnotu položky tohoto slovníku.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="b8bf3-115">Pomocí slovníku **odebrat** a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> metody pro odebrání položky a poté znovu přidejte s požadovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="b8bf3-116">Pomocí slovníku <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="b8bf3-117">Následující příklad znázorňuje obou směrech.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-117">The example below illustrates both ways.</span></span>  
  
3.  <span data-ttu-id="b8bf3-118">Vytvoření <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objektu a nastavit jeho <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> na "IsShared" a jeho <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="b8bf3-119">Použití <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objekt, který má být hodnota <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>na položku "IsShared".</span><span class="sxs-lookup"><span data-stu-id="b8bf3-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5.  <span data-ttu-id="b8bf3-120">Vytvoření <xref:System.Printing.IndexedProperties.PrintStringProperty> objektu a nastavit jeho <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> k "ShareName" a jeho <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> příslušné <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6.  <span data-ttu-id="b8bf3-121">Použití <xref:System.Printing.IndexedProperties.PrintStringProperty> objekt, který má být hodnota <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>na položku "ShareName".</span><span class="sxs-lookup"><span data-stu-id="b8bf3-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7.  <span data-ttu-id="b8bf3-122">Vytvořte další <xref:System.Printing.IndexedProperties.PrintStringProperty> objektu a nastavit jeho <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Místo" a jeho <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> příslušné <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8.  <span data-ttu-id="b8bf3-123">Použít druhý <xref:System.Printing.IndexedProperties.PrintStringProperty> objekt, který má být hodnota <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>na položku "Umístění".</span><span class="sxs-lookup"><span data-stu-id="b8bf3-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="b8bf3-124">Vytvoření pole <xref:System.String>s.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="b8bf3-125">Každá položka je název port na serveru.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="b8bf3-126">Použití <xref:System.Printing.PrintServer.InstallPrintQueue%2A> k instalaci nové tiskárny s novými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="b8bf3-127">Příkladem je níže.</span><span class="sxs-lookup"><span data-stu-id="b8bf3-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="b8bf3-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8bf3-128">See Also</span></span>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="b8bf3-129">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="b8bf3-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="b8bf3-130">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="b8bf3-130">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
