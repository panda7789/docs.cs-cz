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
author: KrzysztofCwalina
ms.openlocfilehash: 64efdc46583a0931df9f57c32424ca4233bf2b82
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143438"
---
# <a name="names-of-namespaces"></a>Názvy oborů názvů
Jako s další pokyny pro pojmenování, cílem při pojmenování obory názvů vytváří dostatečná přehlednost pro programátora pomocí rozhraní hned vědět, co je pravděpodobné, že obsah oboru názvů. Následující šablony určuje obecné pravidlo pro pojmenování obory názvů:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Následují příklady:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** předpony oboru názvů názvy s název společnosti, aby se zabránilo obory názvů v jiné společnosti z který má stejný název.  
  
 **✓ DO** použít název stabilní, nezávislé na verzi produktu, na druhé úrovni název oboru názvů.  
  
 **X DO NOT** používat organizační hierarchie jako základ pro názvy v oboru názvů hierarchií, protože názvy skupin v rámci společnosti jsou obvykle krátkodobou. Uspořádání hierarchie oborů názvů okolo skupin souvisejících technologiích.  
  
 **✓ DO** PascalCasing a komponenty samostatného oboru názvů pomocí tečky (například `Microsoft.Office.PowerPoint`). Pokud vlastní značky využívá netradičních velká a malá písmena, postupujte i v případě, že odchylují od malých a velkých písmen normální obor názvů malých a velkých písmen definované vlastní značky.  
  
 **✓ CONSIDER** pomocí názvy v množném čísle obor názvů, kde je to vhodné.  
  
 Například použít `System.Collections` místo `System.Collection`. Názvy a zkratky jsou však výjimkou tohoto pravidla. Například použít `System.IO` místo `System.IOs`.  
  
 **X DO NOT** používají stejný název pro obor názvů a typ v daném oboru názvů.  
  
 Například nepoužívejte `Debug` jako obor názvů pojmenujte a také zadat třídu s názvem `Debug` ve stejném oboru názvů. Několik kompilátory vyžadují tyto typy jako plně kvalifikovaný.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Obory názvů a typ název je v konfliktu  
 **X DO NOT** zavést názvy obecného typu, jako `Element`, `Node`, `Log`, a `Message`.  
  
 Je velmi vysoká pravděpodobnost, že díky tomu povede k zadání názvu je v konfliktu v běžných scénářích. By měl kvalifikovat názvy obecných typů (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Existují konkrétní pokyny ke vyhnutí se konfliktům název typu pro různé kategorie oborů názvů.  
  
-   **Obory názvů modelu aplikace**  
  
     Obory názvů, které patří do jedné aplikační model se často používají společně, ale jsou téměř nikdy používat s obory názvů modelů jiné aplikace. Například <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů je velmi zřídka použít v kombinaci s <xref:System.Web.UI?displayProperty=nameWithType> oboru názvů. Následuje seznam známých aplikaci modelu obor názvů skupin:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** předáte typy v oborech názvů v rámci jedné aplikace model se stejným názvem.  
  
     Například nepřidávejte typ s názvem `Page` k <xref:System.Web.UI.Adapters?displayProperty=nameWithType> obor názvů, protože <xref:System.Web.UI?displayProperty=nameWithType> již obsahuje typ s názvem oboru názvů `Page`.  
  
-   **Obory názvů infrastruktury**  
  
     Tato skupina obsahuje obory názvů, které se importují jen zřídka během vývoje běžných aplikací. Například `.Design` oborů názvů se používá hlavně při vývoji programovacích nástrojů. Vyhnutí se konfliktům s typy v těchto oborech názvů není důležité.  
  
-   **Obory názvů jádra**  
  
     Základní oborů názvů patří všechny `System` obory názvů, s výjimkou obory názvů modelů aplikací a infrastruktury obory názvů. Obory názvů Core patří mimo jiné `System`, `System.IO`, `System.Xml`, a `System.Net`.  
  
     **X DO NOT** udělení typy názvy, které by byl v konfliktu s žádným typem v oborech názvů jádra.  
  
     Například nikdy nepoužívejte `Stream` jako název typu. By byla v konfliktu s <xref:System.IO.Stream?displayProperty=nameWithType>, velmi často používána typu.  
  
-   **Obor názvů skupin technologie**  
  
     Tato kategorie zahrnuje všechny obory názvů se stejným první dva uzly oboru názvů `(<Company>.<Technology>*`), jako například `Microsoft.Build.Utilities` a `Microsoft.Build.Tasks`. Je důležité, že typy, které patří do jedné technologie nejsou v konfliktu mezi sebou.  
  
     **X DO NOT** přiřadit názvy typů, které by byl v konfliktu s jinými typy v rámci jedné technologie.  
  
     **X DO NOT** zavést typ konflikty v názvech mezi typy v oborech názvů technologii a na obor názvů modelu aplikace (Pokud je tato technologie není určena pro použití s modelem aplikace).  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
