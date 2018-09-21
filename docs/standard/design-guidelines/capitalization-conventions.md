---
title: Konvence pro malá a velká písmena
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 070fc69728c2cb38e465dab9f6f591a77a857531
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46531569"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="5b83c-102">Konvence pro malá a velká písmena</span><span class="sxs-lookup"><span data-stu-id="5b83c-102">Capitalization Conventions</span></span>
<span data-ttu-id="5b83c-103">Pokyny v této kapitole rozložení si jednoduchý způsob pro použití malá a velká, že při použití konzistentně, zkontrolujte identifikátory pro typy, členy a parametry snadno čitelný.</span><span class="sxs-lookup"><span data-stu-id="5b83c-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="5b83c-104">Malá a velká písmena pravidel pro identifikátory</span><span class="sxs-lookup"><span data-stu-id="5b83c-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="5b83c-105">K rozlišení slova v identifikátoru, velké první písmeno první písmeno každého slova v identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="5b83c-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="5b83c-106">Nepoužívejte podtržítka k rozlišení slova, nebo pro tento účel, kdekoli v identifikátory.</span><span class="sxs-lookup"><span data-stu-id="5b83c-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="5b83c-107">Existují dva způsoby vhodné pro velké první písmeno identifikátory, v závislosti na použití identifikátoru:</span><span class="sxs-lookup"><span data-stu-id="5b83c-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="5b83c-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="5b83c-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="5b83c-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="5b83c-109">camelCasing</span></span>  
  
 <span data-ttu-id="5b83c-110">Konvence PascalCasing používá pro všechny identifikátory s výjimkou názvů parametrů velká první znak každého slova (včetně přes dvě písmena délku zkratky), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5b83c-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="5b83c-111">Zvláštní případ se provádí dvoupísmenné zkratky, ve kterých jsou velké obě písmena, jak je znázorněno v následující identifikátor:</span><span class="sxs-lookup"><span data-stu-id="5b83c-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="5b83c-112">Konvence camelCasing používá pouze pro názvy parametrů velká první znak každého slova s výjimkou první slovo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5b83c-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="5b83c-113">Příklad také ukazuje, dvoupísmenné zkratky, které začínají identifikátorem ve formátu camelCase jsou malá písmena.</span><span class="sxs-lookup"><span data-stu-id="5b83c-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="5b83c-114">**✓ DO** použít PascalCasing pro všechny veřejné člen, typ a obor názvů názvy skládající se z více slov.</span><span class="sxs-lookup"><span data-stu-id="5b83c-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="5b83c-115">**✓ DO** použít camelCasing pro názvy parametrů.</span><span class="sxs-lookup"><span data-stu-id="5b83c-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="5b83c-116">Následující tabulka popisuje malá a velká písmena pravidla pro různé typy identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="5b83c-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="5b83c-117">identifikátor</span><span class="sxs-lookup"><span data-stu-id="5b83c-117">Identifier</span></span>|<span data-ttu-id="5b83c-118">Velikost písmen</span><span class="sxs-lookup"><span data-stu-id="5b83c-118">Casing</span></span>|<span data-ttu-id="5b83c-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b83c-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="5b83c-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="5b83c-120">Namespace</span></span>|<span data-ttu-id="5b83c-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="5b83c-122">Typ</span><span class="sxs-lookup"><span data-stu-id="5b83c-122">Type</span></span>|<span data-ttu-id="5b83c-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="5b83c-124">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b83c-124">Interface</span></span>|<span data-ttu-id="5b83c-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="5b83c-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b83c-126">Method</span></span>|<span data-ttu-id="5b83c-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="5b83c-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5b83c-128">Property</span></span>|<span data-ttu-id="5b83c-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="5b83c-130">Událost</span><span class="sxs-lookup"><span data-stu-id="5b83c-130">Event</span></span>|<span data-ttu-id="5b83c-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="5b83c-132">Pole</span><span class="sxs-lookup"><span data-stu-id="5b83c-132">Field</span></span>|<span data-ttu-id="5b83c-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="5b83c-134">Hodnota výčtu</span><span class="sxs-lookup"><span data-stu-id="5b83c-134">Enum value</span></span>|<span data-ttu-id="5b83c-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="5b83c-136">Parametr</span><span class="sxs-lookup"><span data-stu-id="5b83c-136">Parameter</span></span>|<span data-ttu-id="5b83c-137">Camel</span><span class="sxs-lookup"><span data-stu-id="5b83c-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="5b83c-138">Velká písmena složených slov a běžných termínů</span><span class="sxs-lookup"><span data-stu-id="5b83c-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="5b83c-139">Většina složené podmínky jsou považovány za jednoho slova pro účely malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="5b83c-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="5b83c-140">**X DO NOT** převedení na velká písmena jednotlivých slov ve složených slov takzvané uzavřený formuláře.</span><span class="sxs-lookup"><span data-stu-id="5b83c-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="5b83c-141">Toto jsou složené slova napsaná jako jediné slovo, jako je například koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5b83c-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="5b83c-142">Pro účely pokyny pro velká a malá písmena považovat za složené slovo Uzavřeno formuláře jednoho slova.</span><span class="sxs-lookup"><span data-stu-id="5b83c-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="5b83c-143">Chcete-li zjistit, pokud je složené slovo napsané v uzavřená forma použití aktuální slovníku.</span><span class="sxs-lookup"><span data-stu-id="5b83c-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="5b83c-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="5b83c-144">Pascal</span></span>|<span data-ttu-id="5b83c-145">Camel</span><span class="sxs-lookup"><span data-stu-id="5b83c-145">Camel</span></span>|<span data-ttu-id="5b83c-146">Not</span><span class="sxs-lookup"><span data-stu-id="5b83c-146">Not</span></span>|  
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
  
## <a name="case-sensitivity"></a><span data-ttu-id="5b83c-147">Rozlišování velikosti písmen</span><span class="sxs-lookup"><span data-stu-id="5b83c-147">Case Sensitivity</span></span>  
 <span data-ttu-id="5b83c-148">Jazyky, které můžou běžet na modulu CLR není požadována podpora rozlišování, i když některé provést.</span><span class="sxs-lookup"><span data-stu-id="5b83c-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="5b83c-149">I v případě, že jazyk podporuje, jiné jazyky, které můžou přistupovat k rozhraní framework nepodporují.</span><span class="sxs-lookup"><span data-stu-id="5b83c-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="5b83c-150">Libovolné rozhraní API, které jsou zvenku přístupný, proto nelze spoléhat na případ samostatně k rozlišení mezi dvěma názvy ve stejném kontextu.</span><span class="sxs-lookup"><span data-stu-id="5b83c-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="5b83c-151">**X DO NOT** předpokládají, že jsou všechny programovací jazyky velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="5b83c-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="5b83c-152">Nejsou.</span><span class="sxs-lookup"><span data-stu-id="5b83c-152">They are not.</span></span> <span data-ttu-id="5b83c-153">Názvy nesmí liší případ samotný.</span><span class="sxs-lookup"><span data-stu-id="5b83c-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="5b83c-154">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="5b83c-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5b83c-155">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="5b83c-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b83c-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b83c-156">See also</span></span>

- [<span data-ttu-id="5b83c-157">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="5b83c-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="5b83c-158">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="5b83c-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
