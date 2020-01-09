---
title: Názvy oborů názvů
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709228"
---
# <a name="names-of-namespaces"></a>Názvy oborů názvů
Stejně jako u jiných pokynů pro pojmenování je cílem při pojmenovávání oborů názvů vytváření dostatečné srozumitelnosti pro programátora pomocí rozhraní, aby okamžitě věděli, co může být obsah oboru názvů. Následující šablona určuje obecné pravidlo pro názvové obory názvů:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Zde jsou příklady:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** předpony oboru názvů názvy s název společnosti, aby se zabránilo obory názvů v jiné společnosti z který má stejný název.  
  
 **✓ DO** použít název stabilní, nezávislé na verzi produktu, na druhé úrovni název oboru názvů.  
  
 **X DO NOT** používat organizační hierarchie jako základ pro názvy v oboru názvů hierarchií, protože názvy skupin v rámci společnosti jsou obvykle krátkodobou. Uspořádejte hierarchii oborů názvů kolem skupin souvisejících technologií.  
  
 **✓ DO** PascalCasing a komponenty samostatného oboru názvů pomocí tečky (například `Microsoft.Office.PowerPoint`). Pokud vaše značka používá netradiční velikost písmen, měli byste postupovat podle velkých a malých písmen definovaných vaší značkou, a to i v případě, že se liší od normálního velikosti oboru názvů.  
  
 **✓ CONSIDER** pomocí názvy v množném čísle obor názvů, kde je to vhodné.  
  
 Použijte například `System.Collections` místo `System.Collection`. Názvy značek a akronymy jsou však výjimkou tohoto pravidla. Použijte například `System.IO` místo `System.IOs`.  
  
 **X DO NOT** používají stejný název pro obor názvů a typ v daném oboru názvů.  
  
 Nepoužívejte například `Debug` jako název oboru názvů a potom zadejte třídu s názvem `Debug` ve stejném oboru názvů. Několik kompilátorů vyžaduje, aby tyto typy byly plně kvalifikované.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Konflikty oborů názvů a typů  
 **X DO NOT** zavést názvy obecného typu, jako `Element`, `Node`, `Log`, a `Message`.  
  
 Existuje velmi vysoká pravděpodobnost, že by to mělo způsobit konflikty názvů typů v běžných scénářích. Měli byste kvalifikovat názvy obecných typů (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Existují konkrétní pokyny pro předcházení konfliktům názvů typů pro různé kategorie oborů názvů.  
  
- **Obory názvů aplikačního modelu**  
  
     Obory názvů patřící k jednomu aplikačnímu modelu se velmi často používají společně, ale nejsou skoro nikdy použity s obory názvů jiných modelů aplikací. Například obor názvů <xref:System.Windows.Forms?displayProperty=nameWithType> je velmi zřídka používán společně s oborem názvů <xref:System.Web.UI?displayProperty=nameWithType>. Následuje seznam známých skupin oborů názvů aplikačního modelu:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** předáte typy v oborech názvů v rámci jedné aplikace model se stejným názvem.  
  
     Nepřidejte například typ s názvem `Page` do <xref:System.Web.UI.Adapters?displayProperty=nameWithType> oboru názvů, protože <xref:System.Web.UI?displayProperty=nameWithType> obor názvů již obsahuje typ s názvem `Page`.  
  
- **Obory názvů infrastruktury**  
  
     Tato skupina obsahuje obory názvů, které se při vývoji běžných aplikací importují zřídka. Například `.Design` obory názvů se používají hlavně při vývoji programovacích nástrojů. Předcházení konfliktům s typy v těchto oborech názvů není důležité.  
  
- **Základní obory názvů**  
  
     Klíčové obory názvů zahrnují všechny obory názvů `System` s výjimkou oborů názvů modelů aplikací a oborů názvů infrastruktury. Mezi základní obory názvů patří mimo jiné `System`, `System.IO`, `System.Xml`a `System.Net`.  
  
     **X DO NOT** udělení typy názvy, které by byl v konfliktu s žádným typem v oborech názvů jádra.  
  
     Například nikdy nepoužívejte `Stream` jako název typu. Je v konfliktu s <xref:System.IO.Stream?displayProperty=nameWithType>, často používaným typem.  
  
- **Skupiny oboru názvů technologií**  
  
     Tato kategorie zahrnuje všechny obory názvů se stejnými prvními dvěma uzly oboru názvů `(<Company>.<Technology>*`), například `Microsoft.Build.Utilities` a `Microsoft.Build.Tasks`. Je důležité, aby typy patřící do jedné technologie nebyly vzájemně v konfliktu.  
  
     **X DO NOT** přiřadit názvy typů, které by byl v konfliktu s jinými typy v rámci jedné technologie.  
  
     **X DO NOT** zavést typ konflikty v názvech mezi typy v oborech názvů technologii a na obor názvů modelu aplikace (Pokud je tato technologie není určena pro použití s modelem aplikace).  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
