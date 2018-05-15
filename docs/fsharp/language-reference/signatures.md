---
title: Podpisy (F#)
description: 'Naučte se používat soubor podpisu F # uchovávání informací o veřejné podpisy sadu elementů F # program, jako jsou moduly, typy a obory názvů.'
ms.date: 05/16/2016
ms.openlocfilehash: 6e182a1a0ac7f3f9fab27026e582d83ee737822e
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2018
---
# <a name="signatures"></a><span data-ttu-id="50b12-103">Podpisy</span><span class="sxs-lookup"><span data-stu-id="50b12-103">Signatures</span></span>

<span data-ttu-id="50b12-104">Soubor podpis obsahuje informace o veřejné podpisy sadu F # program prvky, jako jsou například moduly, obory názvů a typy.</span><span class="sxs-lookup"><span data-stu-id="50b12-104">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="50b12-105">Slouží k určení usnadnění z těchto elementů programu.</span><span class="sxs-lookup"><span data-stu-id="50b12-105">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="50b12-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50b12-106">Remarks</span></span>
<span data-ttu-id="50b12-107">Pro každý F # soubor kód, abyste měli *soubor podpisu*, což je soubor, který má stejný název jako soubor kódu, ale .fsi rozšíření místo .fs.</span><span class="sxs-lookup"><span data-stu-id="50b12-107">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="50b12-108">Podpis souborů lze také přidat do příkazového řádku, pokud jsou přímo pomocí příkazového řádku kompilace.</span><span class="sxs-lookup"><span data-stu-id="50b12-108">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="50b12-109">K rozlišení mezi soubory kódu a podpis soubory, soubory kódu se někdy označují jako *implementace soubory*.</span><span class="sxs-lookup"><span data-stu-id="50b12-109">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="50b12-110">V projektu by měl předcházet soubor podpisu souboru přidružený kód.</span><span class="sxs-lookup"><span data-stu-id="50b12-110">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="50b12-111">Soubor podpisu popisuje obory názvů, moduly, typy a členy v příslušném souboru implementace.</span><span class="sxs-lookup"><span data-stu-id="50b12-111">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="50b12-112">Informace v souboru se používá k určení, jaké části kódu odpovídající implementace souboru je přístupná z kódu mimo soubor implementace a které části jsou interní soubor implementace.</span><span class="sxs-lookup"><span data-stu-id="50b12-112">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="50b12-113">Obory názvů, moduly a typy, které jsou obsaženy v souboru podpis musí být podmnožinou obory názvů, moduly a typy, které jsou obsaženy v souboru implementace.</span><span class="sxs-lookup"><span data-stu-id="50b12-113">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="50b12-114">Na několik výjimek uvedené dále v tomto tématu jsou považovány za soukromé k souboru implementace těchto prvků jazyka, které nejsou uvedené v souboru podpis.</span><span class="sxs-lookup"><span data-stu-id="50b12-114">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="50b12-115">Pokud žádný soubor podpisu je najde v projektu nebo příkazového řádku, použije se výchozí usnadnění.</span><span class="sxs-lookup"><span data-stu-id="50b12-115">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="50b12-116">Další informace o usnadnění výchozí najdete v tématu [řízení přístupu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="50b12-116">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="50b12-117">V souboru není opakujte implementace každé metody nebo funkce a definice typů.</span><span class="sxs-lookup"><span data-stu-id="50b12-117">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="50b12-118">Místo toho použijte podpis pro každou metodu a funkce, která funguje jako specifikaci dokončení funkcí, které je implementované fragment modul, nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="50b12-118">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="50b12-119">Syntaxe pro typ podpisu je stejný jako příkaz, který se používá v deklaracích abstraktní metodu v abstraktní třídy a rozhraní a také zobrazen IntelliSense a fsi.exe překladač F # při zobrazení správně kompilované vstup.</span><span class="sxs-lookup"><span data-stu-id="50b12-119">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="50b12-120">Pokud není k dispozici dostatek informací v podpis typu indikující, zda je zapečetěná a typ, nebo zda je typ rozhraní, musíte přidat atribut určující povaha typ kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="50b12-120">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="50b12-121">Atributy, které používáte pro tento účel jsou popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="50b12-121">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="50b12-122">Atribut</span><span class="sxs-lookup"><span data-stu-id="50b12-122">Attribute</span></span>|<span data-ttu-id="50b12-123">Popis</span><span class="sxs-lookup"><span data-stu-id="50b12-123">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="50b12-124">Pro typ, který nemá žádné členy abstraktní, nebo by neměla být rozšířena.</span><span class="sxs-lookup"><span data-stu-id="50b12-124">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="50b12-125">Pro typ, který je rozhraní.</span><span class="sxs-lookup"><span data-stu-id="50b12-125">For a type that is an interface.</span></span>|
<span data-ttu-id="50b12-126">Kompilátor vytváří chybu, pokud nejsou konzistentní mezi podpisu a deklarace v souboru implementace atributy.</span><span class="sxs-lookup"><span data-stu-id="50b12-126">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="50b12-127">Použití klíčového slova `val` k vytvoření podpisu pro hodnotu nebo hodnotu, funkce.</span><span class="sxs-lookup"><span data-stu-id="50b12-127">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="50b12-128">Klíčové slovo `type` představuje typ podpisu.</span><span class="sxs-lookup"><span data-stu-id="50b12-128">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="50b12-129">Soubor podpisu můžete vygenerovat pomocí `--sig` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="50b12-129">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="50b12-130">Obecně platí můžete Nezapisovat .fsi soubory ručně.</span><span class="sxs-lookup"><span data-stu-id="50b12-130">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="50b12-131">Místo toho generovat .fsi soubory pomocí kompilátor, přidejte do projektu, pokud máte jeden a upravit jejich odebráním metody a funkce, které nechcete, aby byl přístupný.</span><span class="sxs-lookup"><span data-stu-id="50b12-131">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="50b12-132">Existuje několik pravidel pro podpisy typu:</span><span class="sxs-lookup"><span data-stu-id="50b12-132">There are several rules for type signatures:</span></span>


- <span data-ttu-id="50b12-133">Zkratky typů v souboru implementace nesmí odpovídat typu bez zkratkou v souboru.</span><span class="sxs-lookup"><span data-stu-id="50b12-133">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="50b12-134">Záznamy a rozlišovaná sjednocení musí vystavit všech nebo žádných z jejich pole a konstruktory a pořadí, v podpis musí odpovídat pořadí v souboru implementace.</span><span class="sxs-lookup"><span data-stu-id="50b12-134">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="50b12-135">Třídy může odhalit některé, všech nebo žádných z jejich pole a metody v podpis.</span><span class="sxs-lookup"><span data-stu-id="50b12-135">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="50b12-136">Třídy a struktury, které mají konstruktory musí vystavit deklarace jejich základní třídy ( `inherits` deklarace).</span><span class="sxs-lookup"><span data-stu-id="50b12-136">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="50b12-137">Navíc třídy a struktury, které mají konstruktory musí vystavit všechny jejich abstraktní metody a deklarace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="50b12-137">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="50b12-138">Typy rozhraní musí odhalit jejich metody a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="50b12-138">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="50b12-139">Pravidla pro podpisy hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="50b12-139">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="50b12-140">Modifikátory pro usnadnění (`public`, `internal`a tak dále) a `inline` a `mutable` modifikátory v podpisu musí odpovídat názvům implementace.</span><span class="sxs-lookup"><span data-stu-id="50b12-140">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="50b12-141">Počet parametrů obecného typu (buď implicitně odvodit nebo explicitně deklarovat) musí odpovídat, a typy a typ omezení parametry obecného typu se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="50b12-141">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="50b12-142">Pokud `Literal` atribut se používá, musí být uvedena v podpisu a implementaci a stejnou hodnotu literálu musí použít pro obě.</span><span class="sxs-lookup"><span data-stu-id="50b12-142">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="50b12-143">Vzor parametry (také označované jako *Arita*) podpisů a implementace musí být konzistentní.</span><span class="sxs-lookup"><span data-stu-id="50b12-143">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


- <span data-ttu-id="50b12-144">Pokud názvy parametrů v souboru se liší od odpovídající soubor implementace, název v souboru podpis se použije místo toho, což může způsobit problémy při ladění nebo profilace.</span><span class="sxs-lookup"><span data-stu-id="50b12-144">If parameter names in a signature file differ from the corresponding implementation file, the name in the signature file will be used instead, which may cause issues when debugging or profiling.</span></span> <span data-ttu-id="50b12-145">Pokud chcete být informováni o takové neshody povolit 3218 upozornění v souboru projektu nebo při vyvolání kompilátor (viz `--warnon` pod [– možnosti kompilátoru](compiler-options.md)).</span><span class="sxs-lookup"><span data-stu-id="50b12-145">If you wish to be notified of such mismatches, enable warning 3218 in your project file or when invoking the compiler (see `--warnon` under [Compiler Options](compiler-options.md)).</span></span>


<span data-ttu-id="50b12-146">Následující příklad kódu ukazuje příklad podpis souboru, který má obor názvů, modulu, hodnota funkce a typ podpisy společně s příslušné atributy.</span><span class="sxs-lookup"><span data-stu-id="50b12-146">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="50b12-147">Také ukazuje odpovídající soubor implementace.</span><span class="sxs-lookup"><span data-stu-id="50b12-147">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="50b12-148">Následující kód ukazuje implementaci soubor.</span><span class="sxs-lookup"><span data-stu-id="50b12-148">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="50b12-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="50b12-149">See Also</span></span>
[<span data-ttu-id="50b12-150">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="50b12-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="50b12-151">Řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="50b12-151">Access Control</span></span>](access-control.md)

[<span data-ttu-id="50b12-152">Možnosti kompilátoru</span><span class="sxs-lookup"><span data-stu-id="50b12-152">Compiler Options</span></span>](compiler-options.md)
