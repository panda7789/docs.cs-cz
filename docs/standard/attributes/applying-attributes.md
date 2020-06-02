---
title: Použití atributů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 5557da1531eb55c13d1c7540a50b044d1a7b8a1d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276332"
---
# <a name="applying-attributes"></a><span data-ttu-id="c5137-102">Použití atributů</span><span class="sxs-lookup"><span data-stu-id="c5137-102">Applying Attributes</span></span>
<span data-ttu-id="c5137-103">Na základě následujícího postupu použijte atribut na prvek kódu.</span><span class="sxs-lookup"><span data-stu-id="c5137-103">Use the following process to apply an attribute to an element of your code.</span></span>  
  
1. <span data-ttu-id="c5137-104">Definujte nový atribut nebo použijte stávající atribut importováním oboru názvů z rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5137-104">Define a new attribute or use an existing attribute by importing its namespace from the .NET Framework.</span></span>  
  
2. <span data-ttu-id="c5137-105">Použijte atribut na prvek kódu tak, že ho umístíte bezprostředně před prvek.</span><span class="sxs-lookup"><span data-stu-id="c5137-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>  
  
     <span data-ttu-id="c5137-106">Jednotlivé jazyky mají vlastní syntaxi atributů.</span><span class="sxs-lookup"><span data-stu-id="c5137-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="c5137-107">V jazyce C++ a jazyce C# je atribut ohraničen hranatými závorkami a oddělen od prvku prázdným znakem, který může obsahovat konec řádku.</span><span class="sxs-lookup"><span data-stu-id="c5137-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="c5137-108">V jazyce Visual Basic je atribut ohraničen ostrými závorkami a musí být umístěn na stejném logickém řádku. Znak pro pokračování řádku lze použít v případě, že je vyžadován konec řádku.</span><span class="sxs-lookup"><span data-stu-id="c5137-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>
  
3. <span data-ttu-id="c5137-109">Zadejte poziční parametry a pojmenované parametry atributu.</span><span class="sxs-lookup"><span data-stu-id="c5137-109">Specify positional parameters and named parameters for the attribute.</span></span>  
  
     <span data-ttu-id="c5137-110">Poziční parametry jsou povinné a musí předcházet jakýmkoli pojmenovaným parametrům – odpovídají parametrům jednoho z konstruktorů atributu.</span><span class="sxs-lookup"><span data-stu-id="c5137-110">Positional parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="c5137-111">Pojmenované parametry jsou volitelné a odpovídají vlastnostem atributu pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="c5137-111">Named parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="c5137-112">V jazyce C++ a C# zadejte `name` = `value` pro každý volitelný parametr, kde `name` je název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c5137-112">In C++, and C#, specify `name`=`value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="c5137-113">V jazyce Visual Basic zadejte `name`:=`value`.</span><span class="sxs-lookup"><span data-stu-id="c5137-113">In Visual Basic, specify `name`:=`value`.</span></span>  
  
 <span data-ttu-id="c5137-114">Atribut je při kompilaci kódu vložen do metadat a je k dispozici pro modul CLR (Common Language Runtime) a vlastní nástroje nebo aplikace prostřednictvím služeb reflexe runtime.</span><span class="sxs-lookup"><span data-stu-id="c5137-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>  
  
 <span data-ttu-id="c5137-115">Na základě pravidel zadávání názvů končí všechny názvy atributů slovem Attribute.</span><span class="sxs-lookup"><span data-stu-id="c5137-115">By convention, all attribute names end with Attribute.</span></span> <span data-ttu-id="c5137-116">Avšak několik jazyků, které používají modul runtime, jako jsou například Visual Basic a C#, nevyžadují zadávání úplného názvu atributu.</span><span class="sxs-lookup"><span data-stu-id="c5137-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="c5137-117">Například pokud chcete inicializovat <xref:System.ObsoleteAttribute?displayProperty=nameWithType> , stačí na něj odkazovat jako na **zastaralé**.</span><span class="sxs-lookup"><span data-stu-id="c5137-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>  
  
## <a name="applying-an-attribute-to-a-method"></a><span data-ttu-id="c5137-118">Použití atributu na metodu</span><span class="sxs-lookup"><span data-stu-id="c5137-118">Applying an Attribute to a Method</span></span>  
 <span data-ttu-id="c5137-119">Následující příklad kódu ukazuje, jak deklarovat **System. ObsoleteAttribute**, který označuje kód jako zastaralý.</span><span class="sxs-lookup"><span data-stu-id="c5137-119">The following code example shows how to declare **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="c5137-120">Řetězec `"Will be removed in next version"` je předán atributu.</span><span class="sxs-lookup"><span data-stu-id="c5137-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="c5137-121">Tento atribut vygeneruje upozornění kompilátoru, které zobrazí předaný řetězec, pokud je volán kód popisovaný atributem.</span><span class="sxs-lookup"><span data-stu-id="c5137-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a><span data-ttu-id="c5137-122">Používání atributů na úrovni sestavení</span><span class="sxs-lookup"><span data-stu-id="c5137-122">Applying Attributes at the Assembly Level</span></span>  
 <span data-ttu-id="c5137-123">Chcete-li použít atribut na úrovni sestavení, použijte klíčové slovo **Assembly** ( `Assembly` in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c5137-123">If you want to apply an attribute at the assembly level, use the **assembly** (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="c5137-124">Následující kód ukazuje **AssemblyTitleAttribute** použitou na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="c5137-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 <span data-ttu-id="c5137-125">Pokud použijete tento atribut, bude řetězec `"My Assembly"` umístěn v manifestu sestavení v části souboru s metadaty.</span><span class="sxs-lookup"><span data-stu-id="c5137-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="c5137-126">Atribut můžete zobrazit buď pomocí [jazyka MSIL Disassembler (Ildasm. exe)](../../framework/tools/ildasm-exe-il-disassembler.md) , nebo vytvořením vlastního programu pro načtení atributu.</span><span class="sxs-lookup"><span data-stu-id="c5137-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5137-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5137-127">See also</span></span>

- [<span data-ttu-id="c5137-128">Atributy</span><span class="sxs-lookup"><span data-stu-id="c5137-128">Attributes</span></span>](index.md)
- [<span data-ttu-id="c5137-129">Načítání informací uložených v atributech</span><span class="sxs-lookup"><span data-stu-id="c5137-129">Retrieving Information Stored in Attributes</span></span>](retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="c5137-130">Koncepty</span><span class="sxs-lookup"><span data-stu-id="c5137-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)
- [<span data-ttu-id="c5137-131">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="c5137-131">Attributes (C#)</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="c5137-132">Přehled atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5137-132">Attributes overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)
