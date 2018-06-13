---
title: Konvence malá a velká písmena
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
ms.openlocfilehash: 7ef7913a2601c3a791cb028b4074ce37b9e9421b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575281"
---
# <a name="capitalization-conventions"></a>Konvence malá a velká písmena
Podle pokynů v této kapitoly rozložení se jednoduše pomocí případu, kdy použít konzistentně, zkontrolujte identifikátory pro typy, členů a parametry snadno čitelný.  
  
## <a name="capitalization-rules-for-identifiers"></a>Pravidla převodu pro identifikátory  
 K odlišení slova v identifikátoru v, počáteční písmeno každého slova v identifikátoru. Nepoužívejte podtržítka k odlišení slova, nebo k tomuto účelu, kdekoli v identifikátory. Existují dva způsoby odpovídající identifikátory, v závislosti na použití identifikátoru převedení na velká písmena:  
  
-   PascalCasing  
  
-   camelCasing  
  
 Konvence PascalCasing, použít pro všechny identifikátory kromě názvy parametrů, změní na velké první znak každého slova (včetně režim přes dvě písmena délku), jak je znázorněno v následujících příkladech:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Zvláštním případem je vytvořené pro dvoupísmenným režim, ve kterých jsou aktivované i písmena, jak je znázorněno v následující identifikátor:  
  
 `IOStream`  
  
 CamelCasing konvencí se používá pouze pro názvy parametrů, změní na velké první znak každého slova s výjimkou prvního slova, jak je znázorněno v následujících příkladech. Tento příklad také ukazuje, jsou dvoupísmenným režim, které začínají identifikátorem ve formátu camelCase i malá písmena.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **PROVEĎTE ✓** použít PascalCasing pro všechny veřejné člen, typ a obor názvů názvy skládající se z více slov.  
  
 **PROVEĎTE ✓** použít camelCasing pro názvy parametrů.  
  
 Následující tabulka popisuje pravidla použití velkých písmen pro různé typy identifikátorů.  
  
|Identifikátor|Velikost písmen|Příklad|  
|----------------|------------|-------------|  
|Obor názvů|Pascal|`namespace System.Security { ... }`|  
|Typ|Pascal|`public class StreamReader { ... }`|  
|Rozhraní|Pascal|`public interface IEnumerable { ... }`|  
|Metoda|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Vlastnost|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Událost|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Pole|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Hodnota výčtu|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parametr|Formátu camelCase|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Na velká písmena složených slov a běžné podmínky  
 Většina složené podmínky jsou považovány za jednoho slova pro účely malá a velká písmena.  
  
 **X nesmí** převedení na velká písmena jednotlivých slov ve složených slov takzvané uzavřený formuláře.  
  
 Toto jsou složených slov zapisují jako jednoho slova, jako je například koncový bod. Pro účely pokyny velká a malá písmena považovat za složené slovo uzavřený formuláře jednoho slova. Slovník aktuální použijte k určení, pokud složené slovo je napsána v uzavřené formuláře.  
  
|Pascal|Formátu camelCase|není|  
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
  
## <a name="case-sensitivity"></a>Rozlišování velkých a malých písmen  
 Jazyky, které můžou běžet na modulu CLR nejsou povinné pro podporu rozlišování, i když některé provést. I v případě, že váš jazyk podporuje, další jazyky, které může získat přístup k vaší framework nepodporují. Všechny rozhraní API, které jsou dostupné externě, nelze proto spoléhají na případ samostatně k rozlišení mezi dva názvy v rámci stejné.  
  
 **X nesmí** předpokládají, že jsou všechny programovací jazyky velká a malá písmena. Nejsou. Názvy nemůže lišit o případ samostatně.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
