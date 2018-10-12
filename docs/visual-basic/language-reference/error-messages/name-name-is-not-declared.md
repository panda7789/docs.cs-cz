---
title: Název &#39; &lt;název&gt; &#39; není deklarována
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
author: rpetrusha
ms.author: ronpet
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 3f950bd5604fae7c7d48f6898a4514053061fe10
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122798"
---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="d6c97-102">Název &#39; &lt;název&gt; &#39; není deklarována</span><span class="sxs-lookup"><span data-stu-id="d6c97-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="d6c97-103">Příkaz odkazuje na programovací prvek, ale kompilátor nemůže najít element s tímto názvem přesné.</span><span class="sxs-lookup"><span data-stu-id="d6c97-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="d6c97-104">**ID chyby:** BC30451</span><span class="sxs-lookup"><span data-stu-id="d6c97-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6c97-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d6c97-105">To correct this error</span></span>  
  
1. <span data-ttu-id="d6c97-106">Zkontrolujte, zda název v odkazující příkazu.</span><span class="sxs-lookup"><span data-stu-id="d6c97-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="d6c97-107">Visual Basic je velká a malá písmena, ale jiné kolísání pravopis se považuje za zcela jiný název.</span><span class="sxs-lookup"><span data-stu-id="d6c97-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="d6c97-108">Všimněte si, že podtržítko (`_`) je součástí názvu a proto součástí pravopis.</span><span class="sxs-lookup"><span data-stu-id="d6c97-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2. <span data-ttu-id="d6c97-109">Zkontrolujte, zda je operátor přístupu členů (`.`) mezi objekt a jeho členů.</span><span class="sxs-lookup"><span data-stu-id="d6c97-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="d6c97-110">Pokud máte například <xref:System.Windows.Forms.TextBox> ovládací prvek s názvem `TextBox1`, pro přístup k jeho <xref:System.Windows.Forms.TextBoxBase.Text%2A> vlastnost byste měli zadat `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="d6c97-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="d6c97-111">Pokud místo toho zadejte `TextBox1Text`, vytvoříte jiný název.</span><span class="sxs-lookup"><span data-stu-id="d6c97-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3. <span data-ttu-id="d6c97-112">Pokud správně a správnost syntaxe jakékoli přístup ke členu objektu, ověřte, že element byl deklarován.</span><span class="sxs-lookup"><span data-stu-id="d6c97-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="d6c97-113">Další informace najdete v tématu [deklarované elementy](../../programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6c97-113">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4. <span data-ttu-id="d6c97-114">Pokud je deklarovaný programovací element, zkontrolujte, že se nachází v oboru.</span><span class="sxs-lookup"><span data-stu-id="d6c97-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="d6c97-115">Pokud je mimo oblast deklarace programovací element odkazující příkaz, můžete potřebovat kvalifikovat název elementu.</span><span class="sxs-lookup"><span data-stu-id="d6c97-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="d6c97-116">Další informace najdete v tématu [obor v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="d6c97-116">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>  

5. <span data-ttu-id="d6c97-117">Pokud nechcete použít plně kvalifikovaný typ nebo název typů a členů (například váš kód odkazuje na vlastnost jako `MethodInfo.Name` místo `System.Reflection.MethodInfo.Name`), přidejte [Imports – příkaz](../statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="d6c97-117">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="d6c97-118">Pokud se pokoušíte ke kompilaci projektu aplikace sady SDK – vizuální styl (projekt se \*.vbproj soubor, který začíná na řádku `<Project Sdk="Microsoft.NET.Sdk">`) a chybová zpráva se odkazuje na typ nebo člen v sestavení knihovny Microsoft.VisualBasic.dll, konfigurace aplikace pro Kompilovat s odkazem na knihovnu Runtime jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6c97-118">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="d6c97-119">Ve výchozím nastavení podmnožina knihovny je součástí vašeho sestavení v sadě SDK – vizuální styl projektu.</span><span class="sxs-lookup"><span data-stu-id="d6c97-119">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="d6c97-120">Například následující příklad nejde zkompilovat, protože <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> metoda nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="d6c97-120">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="d6c97-121">Není součástí dílčí modul Runtime jazyka Visual Basic součástí vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="d6c97-121">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   <span data-ttu-id="d6c97-122">Chcete-li vyřešit tuto chybu, přidejte `<VBRuntime>Default</VBRuntime>` elementu k projektům `<PropertyGroup>` části, jak ukazuje následující soubor projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6c97-122">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="d6c97-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6c97-123">See also</span></span>  

[<span data-ttu-id="d6c97-124">Souhrn deklarací a konstant</span><span class="sxs-lookup"><span data-stu-id="d6c97-124">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [<span data-ttu-id="d6c97-125">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6c97-125">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="d6c97-126">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="d6c97-126">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="d6c97-127">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="d6c97-127">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
