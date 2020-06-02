---
title: Konvence pro malá a velká písmena
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 10d628700a9cbf0e842416878ec2c7febfa3d6f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280397"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="36705-102">Konvence pro malá a velká písmena</span><span class="sxs-lookup"><span data-stu-id="36705-102">Capitalization Conventions</span></span>
<span data-ttu-id="36705-103">Pokyny v této kapitole vám pomohou vytvořit jednoduchou metodu pro použití Case, která při použití konzistentně usnadňuje čtení identifikátorů pro typy, členy a parametry.</span><span class="sxs-lookup"><span data-stu-id="36705-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="36705-104">Pravidla psaní velkých písmen pro identifikátory</span><span class="sxs-lookup"><span data-stu-id="36705-104">Capitalization Rules for Identifiers</span></span>
 <span data-ttu-id="36705-105">Chcete-li odlišit slova v identifikátoru, velkými písmeny každého slova v identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="36705-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="36705-106">Nepoužívejte podtržítka k odlišení slov nebo pro tuto skutečnost, a to kdekoli v identifikátorech.</span><span class="sxs-lookup"><span data-stu-id="36705-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="36705-107">Existují dva vhodné způsoby, jak měnit identifikátory v závislosti na použití identifikátoru:</span><span class="sxs-lookup"><span data-stu-id="36705-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="36705-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="36705-108">PascalCasing</span></span>

- <span data-ttu-id="36705-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="36705-109">camelCasing</span></span>

 <span data-ttu-id="36705-110">PascalCasing konvence, která se používá pro všechny identifikátory kromě názvů parametrů, převede první znak každého slova (včetně zkratek na dvě písmena), jak je znázorněno v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="36705-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="36705-111">Zvláštní případ se skládá pro zkratky se dvěma písmeny, ve kterých jsou písmena velká, jak je znázorněno v následujícím identifikátoru:</span><span class="sxs-lookup"><span data-stu-id="36705-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="36705-112">Konvence camelCasing použitá pouze pro názvy parametrů, převede první znak každého slova s výjimkou prvního slova, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="36705-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="36705-113">Jak ukazuje tento příklad, zkratky se dvěma písmeny, které začínají identifikátorem ve stylu CamelCase-použita, jsou malá.</span><span class="sxs-lookup"><span data-stu-id="36705-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="36705-114">✔️ používat PascalCasing pro všechny typy veřejných členů, typů a názvů, které se skládají z více slov.</span><span class="sxs-lookup"><span data-stu-id="36705-114">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="36705-115">pro názvy parametrů ✔️ používat camelCasing.</span><span class="sxs-lookup"><span data-stu-id="36705-115">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="36705-116">Následující tabulka popisuje pravidla psaní velkých a malých písmen pro různé typy identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="36705-116">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="36705-117">Identifikátor</span><span class="sxs-lookup"><span data-stu-id="36705-117">Identifier</span></span>|<span data-ttu-id="36705-118">Velikost písmen</span><span class="sxs-lookup"><span data-stu-id="36705-118">Casing</span></span>|<span data-ttu-id="36705-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="36705-119">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="36705-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="36705-120">Namespace</span></span>|<span data-ttu-id="36705-121">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-121">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="36705-122">Typ</span><span class="sxs-lookup"><span data-stu-id="36705-122">Type</span></span>|<span data-ttu-id="36705-123">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-123">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="36705-124">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="36705-124">Interface</span></span>|<span data-ttu-id="36705-125">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-125">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="36705-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="36705-126">Method</span></span>|<span data-ttu-id="36705-127">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="36705-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="36705-128">Property</span></span>|<span data-ttu-id="36705-129">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="36705-130">Událost</span><span class="sxs-lookup"><span data-stu-id="36705-130">Event</span></span>|<span data-ttu-id="36705-131">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="36705-132">Pole</span><span class="sxs-lookup"><span data-stu-id="36705-132">Field</span></span>|<span data-ttu-id="36705-133">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="36705-134">Hodnota výčtu</span><span class="sxs-lookup"><span data-stu-id="36705-134">Enum value</span></span>|<span data-ttu-id="36705-135">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="36705-136">Parametr</span><span class="sxs-lookup"><span data-stu-id="36705-136">Parameter</span></span>|<span data-ttu-id="36705-137">CamelCase</span><span class="sxs-lookup"><span data-stu-id="36705-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="36705-138">Složená slova na velkých písmen a běžné výrazy</span><span class="sxs-lookup"><span data-stu-id="36705-138">Capitalizing Compound Words and Common Terms</span></span>
 <span data-ttu-id="36705-139">Většina složených výrazů se považuje za jednotlivá slova pro účely velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="36705-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="36705-140">❌Neměňte velká písmena jednotlivých slov, která se označují jako uzavřená složená slova.</span><span class="sxs-lookup"><span data-stu-id="36705-140">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="36705-141">Jedná se o složená slova zapsaná jako jedno slovo, například koncový bod.</span><span class="sxs-lookup"><span data-stu-id="36705-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="36705-142">Pro účely pokynů pro používání malých a velkých písmen považovat uzavřený složený Word jako jedno slovo.</span><span class="sxs-lookup"><span data-stu-id="36705-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="36705-143">Pomocí aktuálního slovníku určíte, zda je v zavřeném formuláři napsán složený text.</span><span class="sxs-lookup"><span data-stu-id="36705-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="36705-144">Jazyce</span><span class="sxs-lookup"><span data-stu-id="36705-144">Pascal</span></span>|<span data-ttu-id="36705-145">CamelCase</span><span class="sxs-lookup"><span data-stu-id="36705-145">Camel</span></span>|<span data-ttu-id="36705-146">Not</span><span class="sxs-lookup"><span data-stu-id="36705-146">Not</span></span>|
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

## <a name="case-sensitivity"></a><span data-ttu-id="36705-147">Rozlišovat velká a malá písmena</span><span class="sxs-lookup"><span data-stu-id="36705-147">Case Sensitivity</span></span>
 <span data-ttu-id="36705-148">Jazyky, které mohou být spuštěny na CLR, nejsou vyžadovány pro podporu rozlišování velkých a malých písmen, i když některé z nich.</span><span class="sxs-lookup"><span data-stu-id="36705-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="36705-149">I v případě, že ho váš jazyk podporuje, jiné jazyky, které by mohly mít přístup k vašemu rozhraní, ne.</span><span class="sxs-lookup"><span data-stu-id="36705-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="36705-150">Každé rozhraní API, které je externě přístupné, proto nemůže spoléhat na velká a malá písmena, aby bylo možné rozlišovat mezi dvěma názvy ve stejném kontextu.</span><span class="sxs-lookup"><span data-stu-id="36705-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="36705-151">❌Nepředpokládá se, že všechny programovací jazyky rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="36705-151">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="36705-152">Nejsou.</span><span class="sxs-lookup"><span data-stu-id="36705-152">They are not.</span></span> <span data-ttu-id="36705-153">Názvy se nesmí lišit pouze podle velikosti písmen.</span><span class="sxs-lookup"><span data-stu-id="36705-153">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="36705-154">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="36705-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="36705-155">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="36705-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="36705-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="36705-156">See also</span></span>

- [<span data-ttu-id="36705-157">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="36705-157">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="36705-158">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="36705-158">Naming Guidelines</span></span>](naming-guidelines.md)
