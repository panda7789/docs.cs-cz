---
title: "Názvy oborů názvů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fc0cb9183fde33887a3e84bb30cc3f79892586e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-namespaces"></a>Názvy oborů názvů
Jako s další pokyny pro pojmenování, cílem obory názvů v názvu je vytvoření dostatečně jasně pro programátory pomocí rozhraní okamžitě vědět, co je pravděpodobné, že obsah oboru názvů. Následující šablony určuje obecná pravidla pro názvy oborů názvů:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Následují příklady:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **PROVEĎTE ✓** předpony oboru názvů názvy s název společnosti, aby se zabránilo obory názvů v jiné společnosti z který má stejný název.  
  
 **PROVEĎTE ✓** použít název stabilní, nezávislé na verzi produktu, na druhé úrovni název oboru názvů.  
  
 **X nesmí** používat organizační hierarchie jako základ pro názvy v oboru názvů hierarchií, protože názvy skupin v rámci společnosti jsou obvykle krátkodobou. Uspořádejte hierarchie oborů názvů kolem skupiny souvisejících technologiích.  
  
 **PROVEĎTE ✓** PascalCasing a komponenty samostatného oboru názvů pomocí tečky (například `Microsoft.Office.PowerPoint`). Pokud vaší značkou aktivuje netradičních velká a malá písmena, řiďte se malá a velká písmena definované vaší značkou, i v případě, že odchylují od normální obor názvů velká a malá písmena.  
  
 **✓ ZVAŽTE** pomocí názvy v množném čísle obor názvů, kde je to vhodné.  
  
 Například použít `System.Collections` místo `System.Collection`. Značky jména a zkratky jsou ale výjimky pro toto pravidlo. Například použít `System.IO` místo `System.IOs`.  
  
 **X nesmí** používají stejný název pro obor názvů a typ v daném oboru názvů.  
  
 Například nepoužívejte `Debug` jako obor názvů název a také poskytují třídy s názvem `Debug` ve stejném oboru názvů. Několik kompilátory vyžadují tyto typy jako plně kvalifikovaný.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Obory názvů a typ konflikty názvů  
 **X nesmí** zavést názvy obecného typu, jako `Element`, `Node`, `Log`, a `Message`.  
  
 Je velmi vysoká pravděpodobnost, že povede k zadání názvu Pokud tak učiníte, je v konfliktu společné scénáře. Použijte následující postup názvy obecného typu (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Existují konkrétní pokyny pro vyhnutí se konfliktům název typu pro různé kategorie obory názvů.  
  
-   **Obory názvů model aplikace**  
  
     Obory názvů, které patří do jedné aplikace modelu se velmi často používají společně, ale používají se téměř žádné s obory názvů modelů jiné aplikace. Například <xref:System.Windows.Forms?displayProperty=nameWithType> obor názvů je velmi málo používané společně s <xref:System.Web.UI?displayProperty=nameWithType> oboru názvů. Následuje seznam skupin obor názvů modelu dobře známé aplikací:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X nesmí** předáte typy v oborech názvů v rámci jedné aplikace model se stejným názvem.  
  
     Například nepřidávejte typ s názvem `Page` k <xref:System.Web.UI.Adapters?displayProperty=nameWithType> obor názvů, protože <xref:System.Web.UI?displayProperty=nameWithType> obor názvů již obsahuje typ s názvem `Page`.  
  
-   **Obory názvů infrastruktury**  
  
     Tato skupina obsahuje obory názvů, které importují zřídka během vývoje aplikace běžné. Například `.Design` obory názvů se používá hlavně při vývoji programování nástroje. Vyhnutí se konfliktům s typy v těchto oborů názvů není důležité.  
  
-   **Obory názvů jádra**  
  
     Obory názvů základní zahrnout všechny `System` obory názvů, s výjimkou obory názvů modelů aplikace a infrastrukturu obory názvů. Obory názvů jádra, patří mimo jiné, `System`, `System.IO`, `System.Xml`, a `System.Net`.  
  
     **X nesmí** udělení typy názvy, které by byl v konfliktu s žádným typem v oborech názvů jádra.  
  
     Například nikdy nepoužívejte `Stream` jako název typu. By byl v konfliktu s <xref:System.IO.Stream?displayProperty=nameWithType>, velmi často používá typu.  
  
-   **Obor názvů skupin technologie**  
  
     Tato kategorie zahrnuje všechny obory názvů se stejným první dva uzly obor názvů `(<Company>.<Technology>*`), jako například `Microsoft.Build.Utilities` a `Microsoft.Build.Tasks`. Je důležité, aby typy, které patří do jedné technologie nedošlo ke konfliktu mezi sebou.  
  
     **X nesmí** přiřadit názvy typů, které by byl v konfliktu s jinými typy v rámci jedné technologie.  
  
     **X nesmí** zavést typ konflikty v názvech mezi typy v oborech názvů technologii a na obor názvů modelu aplikace (Pokud je tato technologie není určena pro použití s modelem aplikace).  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
