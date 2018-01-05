---
title: "Postupy: Načtení vlastností systémového objektu tisku bez reflexe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d93919f691b51d5f177b074e5d9cef2c140458e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="f1705-102">Postupy: Načtení vlastností systémového objektu tisku bez reflexe</span><span class="sxs-lookup"><span data-stu-id="f1705-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="f1705-103">Chcete-li vytvořit seznam vlastností (a typy těchto vlastností) objektu pomocí reflexe můžou způsobit snížení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1705-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="f1705-104"><xref:System.Printing.IndexedProperties> Obor názvů poskytuje prostředky k načtení těchto informací prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="f1705-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1705-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1705-105">Example</span></span>  
 <span data-ttu-id="f1705-106">Takto vypadají kroky tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="f1705-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="f1705-107">Vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="f1705-107">Create an instance of the type.</span></span> <span data-ttu-id="f1705-108">V následujícím příkladu je typ <xref:System.Printing.PrintQueue> typ, který se dodává s [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], ale téměř shodná kódu by měla fungovat pro typy, které jsou odvozeny od <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="f1705-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="f1705-109">Vytvoření <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z tohoto typu <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1705-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="f1705-110"><xref:System.Collections.DictionaryEntry.Value%2A> Vlastnost každé položky tohoto slovníku je objekt jeden z typů, které jsou odvozené z <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="f1705-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="f1705-111">Výčet členů slovníku.</span><span class="sxs-lookup"><span data-stu-id="f1705-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="f1705-112">Pro každý z nich postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="f1705-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="f1705-113">Přetypování nahoru hodnotu každé položky k <xref:System.Printing.IndexedProperties.PrintProperty> a použít ho k vytvoření <xref:System.Printing.IndexedProperties.PrintProperty> objektu.</span><span class="sxs-lookup"><span data-stu-id="f1705-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="f1705-114">Získat typ <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> jednotlivých <xref:System.Printing.IndexedProperties.PrintProperty> objektu.</span><span class="sxs-lookup"><span data-stu-id="f1705-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="f1705-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1705-115">See Also</span></span>  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="f1705-116">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="f1705-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="f1705-117">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="f1705-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
