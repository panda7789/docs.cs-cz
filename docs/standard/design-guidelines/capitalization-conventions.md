---
title: Konvence pro malá a velká písmena
description: Používejte konvence psaní velkých písmen pro identifikátory, složená slova a běžné podmínky. Pochopte, jak rozlišuje velká a malá písmena v rozhraní .NET.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 4903dc587d84ef36bfaa641cfbda59484266c23c
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767790"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="9068b-104">Konvence pro malá a velká písmena</span><span class="sxs-lookup"><span data-stu-id="9068b-104">Capitalization Conventions</span></span>
<span data-ttu-id="9068b-105">Pokyny v této kapitole vám pomohou vytvořit jednoduchou metodu pro použití Case, která při použití konzistentně usnadňuje čtení identifikátorů pro typy, členy a parametry.</span><span class="sxs-lookup"><span data-stu-id="9068b-105">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="9068b-106">Pravidla psaní velkých písmen pro identifikátory</span><span class="sxs-lookup"><span data-stu-id="9068b-106">Capitalization Rules for Identifiers</span></span>
 <span data-ttu-id="9068b-107">Chcete-li odlišit slova v identifikátoru, velkými písmeny každého slova v identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="9068b-107">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="9068b-108">Nepoužívejte podtržítka k odlišení slov nebo pro tuto skutečnost, a to kdekoli v identifikátorech.</span><span class="sxs-lookup"><span data-stu-id="9068b-108">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="9068b-109">Existují dva vhodné způsoby, jak měnit identifikátory v závislosti na použití identifikátoru:</span><span class="sxs-lookup"><span data-stu-id="9068b-109">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="9068b-110">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="9068b-110">PascalCasing</span></span>

- <span data-ttu-id="9068b-111">camelCasing</span><span class="sxs-lookup"><span data-stu-id="9068b-111">camelCasing</span></span>

 <span data-ttu-id="9068b-112">PascalCasing konvence, která se používá pro všechny identifikátory kromě názvů parametrů, převede první znak každého slova (včetně zkratek na dvě písmena), jak je znázorněno v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="9068b-112">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="9068b-113">Zvláštní případ se skládá pro zkratky se dvěma písmeny, ve kterých jsou písmena velká, jak je znázorněno v následujícím identifikátoru:</span><span class="sxs-lookup"><span data-stu-id="9068b-113">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="9068b-114">Konvence camelCasing použitá pouze pro názvy parametrů, převede první znak každého slova s výjimkou prvního slova, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="9068b-114">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="9068b-115">Jak ukazuje tento příklad, zkratky se dvěma písmeny, které začínají identifikátorem ve stylu CamelCase-použita, jsou malá.</span><span class="sxs-lookup"><span data-stu-id="9068b-115">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="9068b-116">✔️ používat PascalCasing pro všechny typy veřejných členů, typů a názvů, které se skládají z více slov.</span><span class="sxs-lookup"><span data-stu-id="9068b-116">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="9068b-117">pro názvy parametrů ✔️ používat camelCasing.</span><span class="sxs-lookup"><span data-stu-id="9068b-117">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="9068b-118">Následující tabulka popisuje pravidla psaní velkých a malých písmen pro různé typy identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="9068b-118">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="9068b-119">Identifikátor</span><span class="sxs-lookup"><span data-stu-id="9068b-119">Identifier</span></span>|<span data-ttu-id="9068b-120">Velikost písmen</span><span class="sxs-lookup"><span data-stu-id="9068b-120">Casing</span></span>|<span data-ttu-id="9068b-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="9068b-121">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="9068b-122">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="9068b-122">Namespace</span></span>|<span data-ttu-id="9068b-123">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-123">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="9068b-124">Typ</span><span class="sxs-lookup"><span data-stu-id="9068b-124">Type</span></span>|<span data-ttu-id="9068b-125">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-125">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="9068b-126">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="9068b-126">Interface</span></span>|<span data-ttu-id="9068b-127">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-127">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="9068b-128">Metoda</span><span class="sxs-lookup"><span data-stu-id="9068b-128">Method</span></span>|<span data-ttu-id="9068b-129">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-129">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="9068b-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="9068b-130">Property</span></span>|<span data-ttu-id="9068b-131">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-131">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="9068b-132">Událost</span><span class="sxs-lookup"><span data-stu-id="9068b-132">Event</span></span>|<span data-ttu-id="9068b-133">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-133">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="9068b-134">Pole</span><span class="sxs-lookup"><span data-stu-id="9068b-134">Field</span></span>|<span data-ttu-id="9068b-135">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-135">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="9068b-136">Hodnota výčtu</span><span class="sxs-lookup"><span data-stu-id="9068b-136">Enum value</span></span>|<span data-ttu-id="9068b-137">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-137">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="9068b-138">Parametr</span><span class="sxs-lookup"><span data-stu-id="9068b-138">Parameter</span></span>|<span data-ttu-id="9068b-139">CamelCase</span><span class="sxs-lookup"><span data-stu-id="9068b-139">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="9068b-140">Složená slova na velkých písmen a běžné výrazy</span><span class="sxs-lookup"><span data-stu-id="9068b-140">Capitalizing Compound Words and Common Terms</span></span>
 <span data-ttu-id="9068b-141">Většina složených výrazů se považuje za jednotlivá slova pro účely velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="9068b-141">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="9068b-142">❌Neměňte velká písmena jednotlivých slov, která se označují jako uzavřená složená slova.</span><span class="sxs-lookup"><span data-stu-id="9068b-142">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="9068b-143">Jedná se o složená slova zapsaná jako jedno slovo, například koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9068b-143">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="9068b-144">Pro účely pokynů pro používání malých a velkých písmen považovat uzavřený složený Word jako jedno slovo.</span><span class="sxs-lookup"><span data-stu-id="9068b-144">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="9068b-145">Pomocí aktuálního slovníku určíte, zda je v zavřeném formuláři napsán složený text.</span><span class="sxs-lookup"><span data-stu-id="9068b-145">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="9068b-146">Jazyce</span><span class="sxs-lookup"><span data-stu-id="9068b-146">Pascal</span></span>|<span data-ttu-id="9068b-147">CamelCase</span><span class="sxs-lookup"><span data-stu-id="9068b-147">Camel</span></span>|<span data-ttu-id="9068b-148">Not</span><span class="sxs-lookup"><span data-stu-id="9068b-148">Not</span></span>|
|------------|-----------|---------|
|`BitFlag`|`bitFlag`|`Bitflag`|
|`Callback`|`callback`|`CallBack`|
|`Canceled`|`canceled`|`Cancelled`|
|`DoNot`|`doNot`|`Don't`|
|`Email`|`email`|`EMail`|
|`Endpoint`|`endpoint`|`EndPoint`|
|`FileName`|`fileName`|`Filename`|
|`Gridline`|`gridline`|`GridLine`|
|`Hashtable`|`hashtable`|`HashTable`|
|`Id`|`id`|`ID`|
|`Indexes`|`indexes`|`Indices`|
|`LogOff`|`logOff`|`LogOut`|
|`LogOn`|`logOn`|`LogIn`|
|`Metadata`|`metadata`|`MetaData, metaData`|
|`Multipanel`|`multipanel`|`MultiPanel`|
|`Multiview`|`multiview`|`MultiView`|
|`Namespace`|`namespace`|`NameSpace`|
|`Ok`|`ok`|`OK`|
|`Pi`|`pi`|`PI`|
|`Placeholder`|`placeholder`|`PlaceHolder`|
|`SignIn`|`signIn`|`SignOn`|
|`SignOut`|`signOut`|`SignOff`|
|`UserName`|`userName`|`Username`|
|`WhiteSpace`|`whiteSpace`|`Whitespace`|
|`Writable`|`writable`|`Writeable`|

## <a name="case-sensitivity"></a><span data-ttu-id="9068b-149">Rozlišovat velká a malá písmena</span><span class="sxs-lookup"><span data-stu-id="9068b-149">Case Sensitivity</span></span>
 <span data-ttu-id="9068b-150">Jazyky, které mohou být spuštěny na CLR, nejsou vyžadovány pro podporu rozlišování velkých a malých písmen, i když některé z nich.</span><span class="sxs-lookup"><span data-stu-id="9068b-150">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="9068b-151">I v případě, že ho váš jazyk podporuje, jiné jazyky, které by mohly mít přístup k vašemu rozhraní, ne.</span><span class="sxs-lookup"><span data-stu-id="9068b-151">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="9068b-152">Každé rozhraní API, které je externě přístupné, proto nemůže spoléhat na velká a malá písmena, aby bylo možné rozlišovat mezi dvěma názvy ve stejném kontextu.</span><span class="sxs-lookup"><span data-stu-id="9068b-152">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="9068b-153">❌Nepředpokládá se, že všechny programovací jazyky rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="9068b-153">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="9068b-154">Nejsou.</span><span class="sxs-lookup"><span data-stu-id="9068b-154">They are not.</span></span> <span data-ttu-id="9068b-155">Názvy se nesmí lišit pouze podle velikosti písmen.</span><span class="sxs-lookup"><span data-stu-id="9068b-155">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="9068b-156">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="9068b-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9068b-157">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="9068b-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9068b-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="9068b-158">See also</span></span>

- [<span data-ttu-id="9068b-159">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="9068b-159">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="9068b-160">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="9068b-160">Naming Guidelines</span></span>](naming-guidelines.md)
