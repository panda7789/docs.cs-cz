---
title: 'Postupy: Načtení vlastností systémového objektu tisku bez reflexe'
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
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f1aa6025c2b8a00dd170a674a1bdea25d76a9a1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="e60bc-102">Postupy: Načtení vlastností systémového objektu tisku bez reflexe</span><span class="sxs-lookup"><span data-stu-id="e60bc-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="e60bc-103">Chcete-li vytvořit seznam vlastností (a typy těchto vlastností) objektu pomocí reflexe můžou způsobit snížení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e60bc-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="e60bc-104"><xref:System.Printing.IndexedProperties> Obor názvů poskytuje prostředky k načtení těchto informací prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="e60bc-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e60bc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e60bc-105">Example</span></span>  
 <span data-ttu-id="e60bc-106">Takto vypadají kroky tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="e60bc-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="e60bc-107">Vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="e60bc-107">Create an instance of the type.</span></span> <span data-ttu-id="e60bc-108">V následujícím příkladu je typ <xref:System.Printing.PrintQueue> typ, který se dodává s verzí rozhraní Microsoft .NET Framework, ale téměř shodná kódu by měla fungovat pro typy, které jsou odvozeny od <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="e60bc-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with Microsoft .NET Framework, but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="e60bc-109">Vytvoření <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z tohoto typu <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="e60bc-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="e60bc-110"><xref:System.Collections.DictionaryEntry.Value%2A> Vlastnost každé položky tohoto slovníku je objekt jeden z typů, které jsou odvozené z <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="e60bc-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="e60bc-111">Výčet členů slovníku.</span><span class="sxs-lookup"><span data-stu-id="e60bc-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="e60bc-112">Pro každý z nich postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="e60bc-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="e60bc-113">Přetypování nahoru hodnotu každé položky k <xref:System.Printing.IndexedProperties.PrintProperty> a použít ho k vytvoření <xref:System.Printing.IndexedProperties.PrintProperty> objektu.</span><span class="sxs-lookup"><span data-stu-id="e60bc-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="e60bc-114">Získat typ <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> jednotlivých <xref:System.Printing.IndexedProperties.PrintProperty> objektu.</span><span class="sxs-lookup"><span data-stu-id="e60bc-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="e60bc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e60bc-115">See Also</span></span>  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="e60bc-116">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="e60bc-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="e60bc-117">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="e60bc-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
