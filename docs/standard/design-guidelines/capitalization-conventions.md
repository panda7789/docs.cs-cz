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
ms.openlocfilehash: fee7f5b7749c97a87e37581f67cbe1b49250b9ce
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709527"
---
# <a name="capitalization-conventions"></a>Konvence pro malá a velká písmena
Pokyny v této kapitole vám pomohou vytvořit jednoduchou metodu pro použití Case, která při použití konzistentně usnadňuje čtení identifikátorů pro typy, členy a parametry.  
  
## <a name="capitalization-rules-for-identifiers"></a>Pravidla psaní velkých písmen pro identifikátory  
 Chcete-li odlišit slova v identifikátoru, velkými písmeny každého slova v identifikátoru. Nepoužívejte podtržítka k odlišení slov nebo pro tuto skutečnost, a to kdekoli v identifikátorech. Existují dva vhodné způsoby, jak měnit identifikátory v závislosti na použití identifikátoru:  
  
- PascalCasing  
  
- camelCasing  
  
 PascalCasing konvence, která se používá pro všechny identifikátory kromě názvů parametrů, převede první znak každého slova (včetně zkratek na dvě písmena), jak je znázorněno v následujících příkladech:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Zvláštní případ se skládá pro zkratky se dvěma písmeny, ve kterých jsou písmena velká, jak je znázorněno v následujícím identifikátoru:  
  
 `IOStream`  
  
 Konvence camelCasing použitá pouze pro názvy parametrů, převede první znak každého slova s výjimkou prvního slova, jak je znázorněno v následujících příkladech. Jak ukazuje tento příklad, zkratky se dvěma písmeny, které začínají identifikátorem ve stylu CamelCase-použita, jsou malá.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** použít PascalCasing pro všechny veřejné člen, typ a obor názvů názvy skládající se z více slov.  
  
 **✓ DO** použít camelCasing pro názvy parametrů.  
  
 Následující tabulka popisuje pravidla psaní velkých a malých písmen pro různé typy identifikátorů.  
  
|identifikátor|Velikost písmen|Příklad|  
|----------------|------------|-------------|  
|Názvový prostor|Jazyce|`namespace System.Security { ... }`|  
|Type|Jazyce|`public class StreamReader { ... }`|  
|Rozhraní|Jazyce|`public interface IEnumerable { ... }`|  
|Metoda|Jazyce|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Vlastnost|Jazyce|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Událost|Jazyce|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Pole|Jazyce|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Hodnota výčtu|Jazyce|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parametr|CamelCase|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Složená slova na velkých písmen a běžné výrazy  
 Většina složených výrazů se považuje za jednotlivá slova pro účely velkých a malých písmen.  
  
 **X DO NOT** převedení na velká písmena jednotlivých slov ve složených slov takzvané uzavřený formuláře.  
  
 Jedná se o složená slova zapsaná jako jedno slovo, například koncový bod. Pro účely pokynů pro používání malých a velkých písmen považovat uzavřený složený Word jako jedno slovo. Pomocí aktuálního slovníku určíte, zda je v zavřeném formuláři napsán složený text.  
  
|Jazyce|CamelCase|Not|  
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
  
## <a name="case-sensitivity"></a>Rozlišovat velká a malá písmena  
 Jazyky, které mohou být spuštěny na CLR, nejsou vyžadovány pro podporu rozlišování velkých a malých písmen, i když některé z nich. I v případě, že ho váš jazyk podporuje, jiné jazyky, které by mohly mít přístup k vašemu rozhraní, ne. Každé rozhraní API, které je externě přístupné, proto nemůže spoléhat na velká a malá písmena, aby bylo možné rozlišovat mezi dvěma názvy ve stejném kontextu.  
  
 **X DO NOT** předpokládají, že jsou všechny programovací jazyky velká a malá písmena. Nejsou. Názvy se nesmí lišit pouze podle velikosti písmen.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
