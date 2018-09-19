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
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990385"
---
# <a name="capitalization-conventions"></a>Konvence pro malá a velká písmena
Pokyny v této kapitole rozložení si jednoduchý způsob pro použití malá a velká, že při použití konzistentně, zkontrolujte identifikátory pro typy, členy a parametry snadno čitelný.  
  
## <a name="capitalization-rules-for-identifiers"></a>Malá a velká písmena pravidel pro identifikátory  
 K rozlišení slova v identifikátoru, velké první písmeno první písmeno každého slova v identifikátoru. Nepoužívejte podtržítka k rozlišení slova, nebo pro tento účel, kdekoli v identifikátory. Existují dva způsoby vhodné pro velké první písmeno identifikátory, v závislosti na použití identifikátoru:  
  
-   PascalCasing  
  
-   camelCasing  
  
 Konvence PascalCasing používá pro všechny identifikátory s výjimkou názvů parametrů velká první znak každého slova (včetně přes dvě písmena délku zkratky), jak je znázorněno v následujícím příkladu:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Zvláštní případ se provádí dvoupísmenné zkratky, ve kterých jsou velké obě písmena, jak je znázorněno v následující identifikátor:  
  
 `IOStream`  
  
 Konvence camelCasing používá pouze pro názvy parametrů velká první znak každého slova s výjimkou první slovo, jak je znázorněno v následujícím příkladu. Příklad také ukazuje, dvoupísmenné zkratky, které začínají identifikátorem ve formátu camelCase jsou malá písmena.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** použít PascalCasing pro všechny veřejné člen, typ a obor názvů názvy skládající se z více slov.  
  
 **✓ DO** použít camelCasing pro názvy parametrů.  
  
 Následující tabulka popisuje malá a velká písmena pravidla pro různé typy identifikátorů.  
  
|identifikátor|Velikost písmen|Příklad|  
|----------------|------------|-------------|  
|Obor názvů|Pascal|`namespace System.Security { ... }`|  
|Typ|Pascal|`public class StreamReader { ... }`|  
|Rozhraní|Pascal|`public interface IEnumerable { ... }`|  
|Metoda|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Vlastnost|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Událost|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Pole|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Hodnota výčtu|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parametr|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Velká písmena složených slov a běžných termínů  
 Většina složené podmínky jsou považovány za jednoho slova pro účely malá a velká písmena.  
  
 **X DO NOT** převedení na velká písmena jednotlivých slov ve složených slov takzvané uzavřený formuláře.  
  
 Toto jsou složené slova napsaná jako jediné slovo, jako je například koncový bod. Pro účely pokyny pro velká a malá písmena považovat za složené slovo Uzavřeno formuláře jednoho slova. Chcete-li zjistit, pokud je složené slovo napsané v uzavřená forma použití aktuální slovníku.  
  
|Pascal|Camel|Not|  
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
  
## <a name="case-sensitivity"></a>Rozlišování velikosti písmen  
 Jazyky, které můžou běžet na modulu CLR není požadována podpora rozlišování, i když některé provést. I v případě, že jazyk podporuje, jiné jazyky, které můžou přistupovat k rozhraní framework nepodporují. Libovolné rozhraní API, které jsou zvenku přístupný, proto nelze spoléhat na případ samostatně k rozlišení mezi dvěma názvy ve stejném kontextu.  
  
 **X DO NOT** předpokládají, že jsou všechny programovací jazyky velká a malá písmena. Nejsou. Názvy nesmí liší případ samotný.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
