---
title: "Konvence malá a velká písmena"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1bddb7bb3559e6f39b7884b92f64bee8fbb3510
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="capitalization-conventions"></a><span data-ttu-id="997d2-102">Konvence malá a velká písmena</span><span class="sxs-lookup"><span data-stu-id="997d2-102">Capitalization Conventions</span></span>
<span data-ttu-id="997d2-103">Podle pokynů v této kapitoly rozložení se jednoduše pomocí případu, kdy použít konzistentně, zkontrolujte identifikátory pro typy, členů a parametry snadno čitelný.</span><span class="sxs-lookup"><span data-stu-id="997d2-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="997d2-104">Pravidla převodu pro identifikátory</span><span class="sxs-lookup"><span data-stu-id="997d2-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="997d2-105">K odlišení slova v identifikátoru v, počáteční písmeno každého slova v identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="997d2-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="997d2-106">Nepoužívejte podtržítka k odlišení slova, nebo k tomuto účelu, kdekoli v identifikátory.</span><span class="sxs-lookup"><span data-stu-id="997d2-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="997d2-107">Existují dva způsoby odpovídající identifikátory, v závislosti na použití identifikátoru převedení na velká písmena:</span><span class="sxs-lookup"><span data-stu-id="997d2-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="997d2-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="997d2-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="997d2-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="997d2-109">camelCasing</span></span>  
  
 <span data-ttu-id="997d2-110">Konvence PascalCasing, použít pro všechny identifikátory kromě názvy parametrů, změní na velké první znak každého slova (včetně režim přes dvě písmena délku), jak je znázorněno v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="997d2-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="997d2-111">Zvláštním případem je vytvořené pro dvoupísmenným režim, ve kterých jsou aktivované i písmena, jak je znázorněno v následující identifikátor:</span><span class="sxs-lookup"><span data-stu-id="997d2-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="997d2-112">CamelCasing konvencí se používá pouze pro názvy parametrů, změní na velké první znak každého slova s výjimkou prvního slova, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="997d2-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="997d2-113">Tento příklad také ukazuje, jsou dvoupísmenným režim, které začínají identifikátorem ve formátu camelCase i malá písmena.</span><span class="sxs-lookup"><span data-stu-id="997d2-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="997d2-114">**PROVEĎTE ✓** použít PascalCasing pro všechny veřejné člen, typ a obor názvů názvy skládající se z více slov.</span><span class="sxs-lookup"><span data-stu-id="997d2-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="997d2-115">**PROVEĎTE ✓** použít camelCasing pro názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="997d2-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="997d2-116">Následující tabulka popisuje pravidla použití velkých písmen pro různé typy identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="997d2-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="997d2-117">Identifikátor</span><span class="sxs-lookup"><span data-stu-id="997d2-117">Identifier</span></span>|<span data-ttu-id="997d2-118">Velikost písmen</span><span class="sxs-lookup"><span data-stu-id="997d2-118">Casing</span></span>|<span data-ttu-id="997d2-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="997d2-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="997d2-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="997d2-120">Namespace</span></span>|<span data-ttu-id="997d2-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="997d2-122">Typ</span><span class="sxs-lookup"><span data-stu-id="997d2-122">Type</span></span>|<span data-ttu-id="997d2-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="997d2-124">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="997d2-124">Interface</span></span>|<span data-ttu-id="997d2-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="997d2-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="997d2-126">Method</span></span>|<span data-ttu-id="997d2-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="997d2-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="997d2-128">Property</span></span>|<span data-ttu-id="997d2-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="997d2-130">Událost</span><span class="sxs-lookup"><span data-stu-id="997d2-130">Event</span></span>|<span data-ttu-id="997d2-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="997d2-132">Pole</span><span class="sxs-lookup"><span data-stu-id="997d2-132">Field</span></span>|<span data-ttu-id="997d2-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="997d2-134">Hodnota výčtu</span><span class="sxs-lookup"><span data-stu-id="997d2-134">Enum value</span></span>|<span data-ttu-id="997d2-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="997d2-136">Parametr</span><span class="sxs-lookup"><span data-stu-id="997d2-136">Parameter</span></span>|<span data-ttu-id="997d2-137">Formátu camelCase</span><span class="sxs-lookup"><span data-stu-id="997d2-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="997d2-138">Na velká písmena složených slov a běžné podmínky</span><span class="sxs-lookup"><span data-stu-id="997d2-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="997d2-139">Většina složené podmínky jsou považovány za jednoho slova pro účely malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="997d2-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="997d2-140">**X nesmí** převedení na velká písmena jednotlivých slov ve složených slov takzvané uzavřený formuláře.</span><span class="sxs-lookup"><span data-stu-id="997d2-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="997d2-141">Toto jsou složených slov zapisují jako jednoho slova, jako je například koncový bod.</span><span class="sxs-lookup"><span data-stu-id="997d2-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="997d2-142">Pro účely pokyny velká a malá písmena považovat za složené slovo uzavřený formuláře jednoho slova.</span><span class="sxs-lookup"><span data-stu-id="997d2-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="997d2-143">Slovník aktuální použijte k určení, pokud složené slovo je napsána v uzavřené formuláře.</span><span class="sxs-lookup"><span data-stu-id="997d2-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="997d2-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="997d2-144">Pascal</span></span>|<span data-ttu-id="997d2-145">Formátu camelCase</span><span class="sxs-lookup"><span data-stu-id="997d2-145">Camel</span></span>|<span data-ttu-id="997d2-146">není</span><span class="sxs-lookup"><span data-stu-id="997d2-146">Not</span></span>|  
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
  
## <a name="case-sensitivity"></a><span data-ttu-id="997d2-147">Rozlišování velkých a malých písmen</span><span class="sxs-lookup"><span data-stu-id="997d2-147">Case Sensitivity</span></span>  
 <span data-ttu-id="997d2-148">Jazyky, které můžou běžet na modulu CLR nejsou povinné pro podporu rozlišování, i když některé provést.</span><span class="sxs-lookup"><span data-stu-id="997d2-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="997d2-149">I v případě, že váš jazyk podporuje, další jazyky, které může získat přístup k vaší framework nepodporují.</span><span class="sxs-lookup"><span data-stu-id="997d2-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="997d2-150">Všechny rozhraní API, které jsou dostupné externě, nelze proto spoléhají na případ samostatně k rozlišení mezi dva názvy v rámci stejné.</span><span class="sxs-lookup"><span data-stu-id="997d2-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="997d2-151">**X nesmí** předpokládají, že jsou všechny programovací jazyky velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="997d2-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="997d2-152">Nejsou.</span><span class="sxs-lookup"><span data-stu-id="997d2-152">They are not.</span></span> <span data-ttu-id="997d2-153">Názvy nemůže lišit o případ samostatně.</span><span class="sxs-lookup"><span data-stu-id="997d2-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="997d2-154">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="997d2-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="997d2-155">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="997d2-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="997d2-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="997d2-156">See Also</span></span>  
 [<span data-ttu-id="997d2-157">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="997d2-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="997d2-158">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="997d2-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
