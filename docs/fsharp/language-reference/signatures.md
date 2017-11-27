---
title: Podpisy (F#)
description: "Naučte se používat soubor podpisu F # uchovávání informací o veřejné podpisy sadu elementů F # program, jako jsou moduly, typy a obory názvů."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 76c84a62-b2f6-44ec-8238-e687e2f7d18e
ms.openlocfilehash: d0f71c6472852268303a2d3af2e4b0a3c256704e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="signatures"></a><span data-ttu-id="f89f1-104">Podpisy</span><span class="sxs-lookup"><span data-stu-id="f89f1-104">Signatures</span></span>

<span data-ttu-id="f89f1-105">Soubor podpis obsahuje informace o veřejné podpisy sadu F # program prvky, jako jsou například moduly, obory názvů a typy.</span><span class="sxs-lookup"><span data-stu-id="f89f1-105">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="f89f1-106">Slouží k určení usnadnění z těchto elementů programu.</span><span class="sxs-lookup"><span data-stu-id="f89f1-106">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="f89f1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f89f1-107">Remarks</span></span>
<span data-ttu-id="f89f1-108">Pro každý F # soubor kód, abyste měli *soubor podpisu*, což je soubor, který má stejný název jako soubor kódu, ale .fsi rozšíření místo .fs.</span><span class="sxs-lookup"><span data-stu-id="f89f1-108">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="f89f1-109">Podpis souborů lze také přidat do příkazového řádku, pokud jsou přímo pomocí příkazového řádku kompilace.</span><span class="sxs-lookup"><span data-stu-id="f89f1-109">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="f89f1-110">K rozlišení mezi soubory kódu a podpis soubory, soubory kódu se někdy označují jako *implementace soubory*.</span><span class="sxs-lookup"><span data-stu-id="f89f1-110">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="f89f1-111">V projektu by měl předcházet soubor podpisu souboru přidružený kód.</span><span class="sxs-lookup"><span data-stu-id="f89f1-111">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="f89f1-112">Soubor podpisu popisuje obory názvů, moduly, typy a členy v příslušném souboru implementace.</span><span class="sxs-lookup"><span data-stu-id="f89f1-112">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="f89f1-113">Informace v souboru se používá k určení, jaké části kódu odpovídající implementace souboru je přístupná z kódu mimo soubor implementace a které části jsou interní soubor implementace.</span><span class="sxs-lookup"><span data-stu-id="f89f1-113">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="f89f1-114">Obory názvů, moduly a typy, které jsou obsaženy v souboru podpis musí být podmnožinou obory názvů, moduly a typy, které jsou obsaženy v souboru implementace.</span><span class="sxs-lookup"><span data-stu-id="f89f1-114">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="f89f1-115">Na několik výjimek uvedené dále v tomto tématu jsou považovány za soukromé k souboru implementace těchto prvků jazyka, které nejsou uvedené v souboru podpis.</span><span class="sxs-lookup"><span data-stu-id="f89f1-115">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="f89f1-116">Pokud žádný soubor podpisu je najde v projektu nebo příkazového řádku, použije se výchozí usnadnění.</span><span class="sxs-lookup"><span data-stu-id="f89f1-116">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="f89f1-117">Další informace o usnadnění výchozí najdete v tématu [řízení přístupu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="f89f1-117">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="f89f1-118">V souboru není opakujte implementace každé metody nebo funkce a definice typů.</span><span class="sxs-lookup"><span data-stu-id="f89f1-118">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="f89f1-119">Místo toho použijte podpis pro každou metodu a funkce, která funguje jako specifikaci dokončení funkcí, které je implementované fragment modul, nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f89f1-119">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="f89f1-120">Syntaxe pro typ podpisu je stejný jako příkaz, který se používá v deklaracích abstraktní metodu v abstraktní třídy a rozhraní a také zobrazen IntelliSense a fsi.exe překladač F # při zobrazení správně kompilované vstup.</span><span class="sxs-lookup"><span data-stu-id="f89f1-120">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="f89f1-121">Pokud není k dispozici dostatek informací v podpis typu indikující, zda je zapečetěná a typ, nebo zda je typ rozhraní, musíte přidat atribut určující povaha typ kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f89f1-121">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="f89f1-122">Atributy, které používáte pro tento účel jsou popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f89f1-122">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="f89f1-123">Atribut</span><span class="sxs-lookup"><span data-stu-id="f89f1-123">Attribute</span></span>|<span data-ttu-id="f89f1-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f89f1-124">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="f89f1-125">Pro typ, který nemá žádné členy abstraktní, nebo by neměla být rozšířena.</span><span class="sxs-lookup"><span data-stu-id="f89f1-125">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="f89f1-126">Pro typ, který je rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f89f1-126">For a type that is an interface.</span></span>|
<span data-ttu-id="f89f1-127">Kompilátor vytváří chybu, pokud nejsou konzistentní mezi podpisu a deklarace v souboru implementace atributy.</span><span class="sxs-lookup"><span data-stu-id="f89f1-127">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="f89f1-128">Použití klíčového slova `val` k vytvoření podpisu pro hodnotu nebo hodnotu, funkce.</span><span class="sxs-lookup"><span data-stu-id="f89f1-128">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="f89f1-129">Klíčové slovo `type` představuje typ podpisu.</span><span class="sxs-lookup"><span data-stu-id="f89f1-129">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="f89f1-130">Soubor podpisu můžete vygenerovat pomocí `--sig` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f89f1-130">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="f89f1-131">Obecně platí můžete Nezapisovat .fsi soubory ručně.</span><span class="sxs-lookup"><span data-stu-id="f89f1-131">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="f89f1-132">Místo toho generovat .fsi soubory pomocí kompilátor, přidejte do projektu, pokud máte jeden a upravit jejich odebráním metody a funkce, které nechcete, aby byl přístupný.</span><span class="sxs-lookup"><span data-stu-id="f89f1-132">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="f89f1-133">Existuje několik pravidel pro podpisy typu:</span><span class="sxs-lookup"><span data-stu-id="f89f1-133">There are several rules for type signatures:</span></span>


- <span data-ttu-id="f89f1-134">Zkratky typů v souboru implementace nesmí odpovídat typu bez zkratkou v souboru.</span><span class="sxs-lookup"><span data-stu-id="f89f1-134">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="f89f1-135">Záznamy a rozlišovaná sjednocení musí vystavit všech nebo žádných z jejich pole a konstruktory a pořadí, v podpis musí odpovídat pořadí v souboru implementace.</span><span class="sxs-lookup"><span data-stu-id="f89f1-135">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="f89f1-136">Třídy může odhalit některé, všech nebo žádných z jejich pole a metody v podpis.</span><span class="sxs-lookup"><span data-stu-id="f89f1-136">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="f89f1-137">Třídy a struktury, které mají konstruktory musí vystavit deklarace jejich základní třídy ( `inherits` deklarace).</span><span class="sxs-lookup"><span data-stu-id="f89f1-137">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="f89f1-138">Navíc třídy a struktury, které mají konstruktory musí vystavit všechny jejich abstraktní metody a deklarace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f89f1-138">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="f89f1-139">Typy rozhraní musí odhalit jejich metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f89f1-139">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="f89f1-140">Pravidla pro podpisy hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f89f1-140">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="f89f1-141">Modifikátory pro usnadnění (`public`, `internal`a tak dále) a `inline` a `mutable` modifikátory v podpisu musí odpovídat názvům implementace.</span><span class="sxs-lookup"><span data-stu-id="f89f1-141">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="f89f1-142">Počet parametrů obecného typu (buď implicitně odvodit nebo explicitně deklarovat) musí odpovídat, a typy a typ omezení parametry obecného typu se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="f89f1-142">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="f89f1-143">Pokud `Literal` atribut se používá, musí být uvedena v podpisu a implementaci a stejnou hodnotu literálu musí použít pro obě.</span><span class="sxs-lookup"><span data-stu-id="f89f1-143">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="f89f1-144">Vzor parametry (také označované jako *Arita*) podpisů a implementace musí být konzistentní.</span><span class="sxs-lookup"><span data-stu-id="f89f1-144">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


<span data-ttu-id="f89f1-145">Následující příklad kódu ukazuje příklad podpis souboru, který má obor názvů, modulu, hodnota funkce a typ podpisy společně s příslušné atributy.</span><span class="sxs-lookup"><span data-stu-id="f89f1-145">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="f89f1-146">Také ukazuje odpovídající soubor implementace.</span><span class="sxs-lookup"><span data-stu-id="f89f1-146">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="f89f1-147">Následující kód ukazuje implementaci soubor.</span><span class="sxs-lookup"><span data-stu-id="f89f1-147">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="f89f1-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="f89f1-148">See Also</span></span>
[<span data-ttu-id="f89f1-149">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="f89f1-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f89f1-150">Řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="f89f1-150">Access Control</span></span>](access-control.md)

[<span data-ttu-id="f89f1-151">Možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="f89f1-151">Compiler Options</span></span>](compiler-options.md)
