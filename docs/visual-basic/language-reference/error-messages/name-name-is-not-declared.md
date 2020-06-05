---
title: Název '<name>' není deklarován.
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 6fa4639b97e4314d8752ae520e94a58a189b7cbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397165"
---
# <a name="name-name-is-not-declared"></a><span data-ttu-id="42a2b-102">Název '\<name>' není deklarován.</span><span class="sxs-lookup"><span data-stu-id="42a2b-102">Name '\<name>' is not declared</span></span>
<span data-ttu-id="42a2b-103">Příkaz odkazuje na programovací prvek, ale kompilátor nemůže najít element s tímto přesným názvem.</span><span class="sxs-lookup"><span data-stu-id="42a2b-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="42a2b-104">**ID chyby:** BC30451</span><span class="sxs-lookup"><span data-stu-id="42a2b-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42a2b-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="42a2b-105">To correct this error</span></span>  
  
1. <span data-ttu-id="42a2b-106">Zkontrolujte pravopis názvu v odkazujícím příkazu.</span><span class="sxs-lookup"><span data-stu-id="42a2b-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="42a2b-107">Visual Basic rozlišuje velká a malá písmena, ale jakékoli jiné variace v pravopisu se považují za úplně jiný název.</span><span class="sxs-lookup"><span data-stu-id="42a2b-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="42a2b-108">Všimněte si, že podtržítko ( `_` ) je součástí názvu a je proto součástí pravopisu.</span><span class="sxs-lookup"><span data-stu-id="42a2b-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2. <span data-ttu-id="42a2b-109">Ověřte, zda máte operátor přístupu členů ( `.` ) mezi objektem a jeho členem.</span><span class="sxs-lookup"><span data-stu-id="42a2b-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="42a2b-110">Například pokud máte <xref:System.Windows.Forms.TextBox> ovládací prvek s názvem `TextBox1` , pro přístup k jeho <xref:System.Windows.Forms.TextBoxBase.Text%2A> vlastnosti byste měli zadat `TextBox1.Text` .</span><span class="sxs-lookup"><span data-stu-id="42a2b-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="42a2b-111">Pokud místo toho zadáte `TextBox1Text` , vytvořili jste jiný název.</span><span class="sxs-lookup"><span data-stu-id="42a2b-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3. <span data-ttu-id="42a2b-112">Pokud je pravopis správné a syntaxe jakéhokoli přístupu ke členu objektu je správná, ověřte, zda byl prvek deklarován.</span><span class="sxs-lookup"><span data-stu-id="42a2b-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="42a2b-113">Další informace naleznete v tématu [deklarované elementy](../../programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="42a2b-113">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4. <span data-ttu-id="42a2b-114">Pokud byl deklarován element, ověřte, zda je v oboru.</span><span class="sxs-lookup"><span data-stu-id="42a2b-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="42a2b-115">Pokud je odkazující příkaz mimo oblast, která deklaruje prvek programování, může být nutné kvalifikovat název elementu.</span><span class="sxs-lookup"><span data-stu-id="42a2b-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="42a2b-116">Další informace najdete v tématu věnovaném [oboru v Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="42a2b-116">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>  

5. <span data-ttu-id="42a2b-117">Pokud nepoužíváte plně kvalifikovaný typ nebo typ a název členu (například váš kód odkazuje na vlastnost `MethodInfo.Name` namísto `System.Reflection.MethodInfo.Name` ), přidejte [příkaz Imports](../statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="42a2b-117">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="42a2b-118">Pokud se pokoušíte zkompilovat projekt ve stylu sady SDK (projekt se \* souborem. vbproj, který začíná na řádku `<Project Sdk="Microsoft.NET.Sdk">` ), a chybová zpráva odkazuje na typ nebo člen v sestavení Microsoft. VisualBasic. dll, nakonfigurujte svou aplikaci tak, aby byla zkompilována s odkazem na knihovnu modulu runtime Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="42a2b-118">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="42a2b-119">Ve výchozím nastavení je podmnožina knihovny vložena do sestavení v projektu ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="42a2b-119">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="42a2b-120">Například následující příklad se nepodaří zkompilovat, protože <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> nelze nalézt metodu.</span><span class="sxs-lookup"><span data-stu-id="42a2b-120">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="42a2b-121">Není vložen do podmnožiny modulu runtime Visual Basic, který je součástí vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="42a2b-121">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   <span data-ttu-id="42a2b-122">Chcete-li tuto chybu vyřešit, přidejte `<VBRuntime>Default</VBRuntime>` prvek do `<PropertyGroup>` části projekty, jak ukazuje následující soubor Visual Basic projektu.</span><span class="sxs-lookup"><span data-stu-id="42a2b-122">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="42a2b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="42a2b-123">See also</span></span>

- [<span data-ttu-id="42a2b-124">Souhrn deklarací a konstant</span><span class="sxs-lookup"><span data-stu-id="42a2b-124">Declarations and Constants Summary</span></span>](../keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="42a2b-125">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42a2b-125">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="42a2b-126">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="42a2b-126">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="42a2b-127">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="42a2b-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
