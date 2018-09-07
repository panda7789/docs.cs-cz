---
title: Základní třídy pro implementaci abstrakcí
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f326ee895251678c7a23ea84a11e83951edf2cc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078636"
---
# <a name="base-classes-for-implementing-abstractions"></a>Základní třídy pro implementaci abstrakcí
Přesněji řečeno třída změní základní třídy, pokud jiné třídy je odvozen z něj. Pro účely této části ale základní třídy je třída navržená především pro poskytování běžné abstrakce nebo pro jiné třídy opakovaně používat některé výchozí implementace ale dědičnosti. Základní třídy se obvykle nacházejí uprostřed hierarchie dědičnosti mezi několika vlastní implementace v dolní části a abstrakce na nejnižší úrovni hierarchie.  
  
 Pro implementaci abstrakcí slouží jako pomocné rutiny implementace. Například jeden z rozhraní Framework abstrakce pro seřazené kolekce položek je <xref:System.Collections.Generic.IList%601> rozhraní. Implementace <xref:System.Collections.Generic.IList%601> není triviální, a proto rozhraní zajišťuje několik základních tříd, jako například <xref:System.Collections.ObjectModel.Collection%601> a <xref:System.Collections.ObjectModel.KeyedCollection%602>, který slouží jako pomocné rutiny pro implementaci vlastní kolekce.  
  
 Základní třídy obvykle nejsou vhodné, která bude sloužit jako abstrakce samy, protože mají tendenci obsahují příliš mnoho implementací. Například `Collection<T>` základní třída obsahuje velké množství implementace týkající se skutečnosti, že implementuje neobecné `IList` rozhraní (aby lépe integrovat neobecné kolekce) a na skutečnost, že je kolekce položek uložených v paměti v jednom z jeho polí.  
  
 Jak bylo uvedeno výše základních tříd může poskytnout nedocenitelné nápovědy pro uživatele, kteří potřebují k implementaci abstrakcí, ale ve stejnou dobu, může představovat i nevýhodu významné. Tyto přidat styčné plochy a zvětšit hloubku hierarchie dědičnosti a proto koncepčně zkomplikovat rozhraní framework. Základní třídy by proto použít pouze v případě, že poskytují uživatelům rozhraní výrazně zlepšit situaci. Mělo by se vyhnout Pokud, zadejte hodnotu pouze pro implementátory rozhraní, ve kterém případu delegování na interní implementaci namísto dědičnosti ze základní třídy silného považovat za.  
  
 **✓ CONSIDER** provedení základní třídy abstraktní i v případě, že neobsahují žádné abstraktní členy. To jasně komunikuje uživatelům určené výhradně, aby se dědila z třídy.  
  
 **✓ CONSIDER** umístění základních tříd do samostatného oboru názvů z nejdůležitějších scénář typů. Podle definice základních tříd jsou určené pro scénáře pokročilých rozšíření a proto nejsou zajímavé pro většinu uživatelů.  
  
 **X AVOID** pojmenování základní třídy s příponou "Základní", pokud třída je určena pro použití v veřejná rozhraní API.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
