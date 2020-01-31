---
title: Základní třídy pro implementaci abstrakcí
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: b22923338f8488b6f7684e565f62d9afc16e6aa0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741780"
---
# <a name="base-classes-for-implementing-abstractions"></a>Základní třídy pro implementaci abstrakcí
V případě, že je z něj odvozena jiná třída, třída se bude zcela vymluvit jako základní třída. Pro účely této části je však základní třídou třída navržená hlavně pro poskytnutí společné abstrakce nebo pro jiné třídy pro opakované použití některé výchozí implementace, i když je dědění. Základní třídy obvykle sedí uprostřed hierarchií dědičnosti mezi abstrakcí v kořenovém adresáři hierarchie a několika vlastními implementacemi v dolní části.

 Slouží jako implementační pomocníky k implementaci abstrakcí. Například jedna z abstrakcí rozhraní pro uspořádané kolekce položek je <xref:System.Collections.Generic.IList%601> rozhraní. Implementace <xref:System.Collections.Generic.IList%601> není triviální, a proto rozhraní poskytuje několik základních tříd, jako je například <xref:System.Collections.ObjectModel.Collection%601> a <xref:System.Collections.ObjectModel.KeyedCollection%602>, které slouží jako pomocník pro implementaci vlastních kolekcí.

 Základní třídy většinou nejsou vhodné k tomu, aby sloužily jako abstrakce samotných, protože by měly obsahovat příliš mnoho implementace. Například základní třída `Collection<T>` obsahuje mnoho implementace souvisejících se skutečností, že implementuje neobecné `IList` rozhraní (pro integraci lépe s neobecnými kolekcemi) a fakt, že se jedná o kolekci položek uložených v paměti v jednom z jeho polí.

 Jak už bylo popsáno, základní třídy mohou poskytnout nevýznamnou nápovědu pro uživatele, kteří potřebují implementovat abstrakce, ale ve stejnou dobu se může jednat o významnou zodpovědnost. Přidávají oblast Surface a zvyšují hloubku hierarchií dědičnosti a tak koncepčně komplikuje rozhraní. Proto by měly být použity základní třídy pouze v případě, že poskytují významnou hodnotu uživatelům rozhraní. Měli byste se vyhnout, pokud poskytují hodnotu pouze implementátorům rozhraní, v takovém případě by mělo být silně zváženo delegování na vnitřní implementaci místo dědičnosti základní třídy.

 ✔️ Zvažte, že se mají abstraktní základní třídy vystavovat, i když neobsahují žádné abstraktní členy. To jasně oznamuje uživatelům, že třída je navržena výhradně pro dědění.

 ✔️ Zvažte umístění základních tříd v samostatném oboru názvů z typů scénářů hlavní. Podle definice jsou základní třídy určené pro pokročilé scénáře rozšiřitelnosti, proto nejsou zajímavé pro většinu uživatelů.

 ❌ se vyhnout pojmenovávání základních tříd s příponou "základní", pokud je třída určena pro použití ve veřejných rozhraních API.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
