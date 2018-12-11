---
title: Návrh pole
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: KrzysztofCwalina
ms.openlocfilehash: 34c5a163e545b78c188f37b2819962b4c7c56f80
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144348"
---
# <a name="field-design"></a>Návrh pole
Princip zapouzdření je jedním z nejdůležitějších pojmy v objektově orientovaný návrh. Tento princip hlásí, že data uložená v objektu by měla být přístupné pouze pro tento objekt.  
  
 Užitečný způsob, jak interpretovat princip je říct, že typ by měl být navržené tak, aby k polím tohoto typu (název nebo typ změn) můžete změnit bez narušení kód jiný než pro členy typu. Tomto výkladu okamžitě znamená, že všechna pole musí být privátní.  
  
 Vylučujeme konstantní a statické pole jen pro čtení z tohoto striktní omezení, protože pole, podle definice téměř nikdy musejí změnit.  
  
 **X DO NOT** zadejte pole instance, která jsou veřejných nebo chráněný.  
  
 Vlastnosti by měla poskytnout pro přístup k pole namísto tak jejich veřejné nebo chráněné.  
  
 **✓ DO** pro konstanty, které se budou měnit nikdy používat konstantní pole.  
  
 Kompilátor se oděl do hodnoty pole const přímo do kódu volání. Proto konstantních hodnot lze nikdy změnit bez rizika porušení kompatibilitu.  
  
 **✓ DO** použít veřejné statické `readonly` pole pro instance předdefinovaných objektů.  
  
 Pokud jsou předdefinované instance daného typu, je deklarujte jako veřejná pole jen pro čtení statické v samotném typu.  
  
 **X DO NOT** přiřadit instancí měnitelný typy `readonly` pole.  
  
 Měnitelný typ je typ s instancemi, které můžete upravit po jsou vytvořeny. Například pole, většina kolekce a datové proudy jsou měnitelné typy, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, a <xref:System.String?displayProperty=nameWithType> jsou všechny neměnné. Modifikátor jen pro čtení na pole typu odkazu brání instance uloženo v poli nahradit, ale nezabrání data instance pole nebylo možné měnit voláním členů změna instance.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
