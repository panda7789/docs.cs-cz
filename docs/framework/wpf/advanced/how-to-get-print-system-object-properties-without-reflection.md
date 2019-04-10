---
title: 'Postupy: Získání vlastností systémového objektu tisku bez reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: bb906dafd98e75708764b5f0f009900719f6a475
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335196"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="2eba7-102">Postupy: Získání vlastností systémového objektu tisku bez reflexe</span><span class="sxs-lookup"><span data-stu-id="2eba7-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="2eba7-103">Chcete-li vytvořit seznam vlastností (a typy těchto vlastností) na objekt pomocí reflexe můžou způsobit snížení výkonu aplikace.</span><span class="sxs-lookup"><span data-stu-id="2eba7-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="2eba7-104"><xref:System.Printing.IndexedProperties> Obor názvů poskytuje prostředky k načtení těchto informací s pomocí operace reflection.</span><span class="sxs-lookup"><span data-stu-id="2eba7-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eba7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2eba7-105">Example</span></span>  
 <span data-ttu-id="2eba7-106">Kroky tohoto postupu jsou následující.</span><span class="sxs-lookup"><span data-stu-id="2eba7-106">The steps for doing this are as follows.</span></span>  
  
1. <span data-ttu-id="2eba7-107">Vytvořte instanci typu.</span><span class="sxs-lookup"><span data-stu-id="2eba7-107">Create an instance of the type.</span></span> <span data-ttu-id="2eba7-108">V následujícím příkladu je typ <xref:System.Printing.PrintQueue> typ, který se dodává se sadou Microsoft .NET Framework, ale téměř stejný kód by měl fungovat pro typy odvozené od <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="2eba7-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with Microsoft .NET Framework, but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2. <span data-ttu-id="2eba7-109">Vytvoření <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z tohoto typu <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="2eba7-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="2eba7-110"><xref:System.Collections.DictionaryEntry.Value%2A> Vlastností pro každou položku ve slovníku je objekt jednoho z typů odvozených z <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="2eba7-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3. <span data-ttu-id="2eba7-111">Vytvořit výčet členů slovníku.</span><span class="sxs-lookup"><span data-stu-id="2eba7-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="2eba7-112">Pro každý z nich postupujte následovně.</span><span class="sxs-lookup"><span data-stu-id="2eba7-112">For each of them, do the following.</span></span>  
  
4. <span data-ttu-id="2eba7-113">Hodnota jednotlivých záznamů pro přetypování nahoru <xref:System.Printing.IndexedProperties.PrintProperty> a použijte ji k vytvoření <xref:System.Printing.IndexedProperties.PrintProperty> objektu.</span><span class="sxs-lookup"><span data-stu-id="2eba7-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5. <span data-ttu-id="2eba7-114">Získat typ <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> jednotlivých <xref:System.Printing.IndexedProperties.PrintProperty> objektu.</span><span class="sxs-lookup"><span data-stu-id="2eba7-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="2eba7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2eba7-115">See also</span></span>

- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="2eba7-116">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="2eba7-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="2eba7-117">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="2eba7-117">Printing Overview</span></span>](printing-overview.md)
