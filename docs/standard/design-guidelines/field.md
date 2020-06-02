---
title: Návrh pole
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 3a5ae985ab161899fbb5e96f9b0ef0cfa90b957c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289743"
---
# <a name="field-design"></a>Návrh pole
Principem zapouzdření je jeden z nejdůležitějších pojmů v objektově orientovaném návrhu. Tato zásada uvádí, že data uložená v objektu by měla být přístupná pouze k tomuto objektu.

 Užitečný způsob, jak interpretovat princip, je říci, že by měl být navržen typ tak, aby bylo možné provést změny v polích daného typu (změny názvu nebo typu) bez narušení kódu, který je jiný než pro členy typu. Tato interpretace okamžitě znamená, že všechna pole musí být soukromá.

 Z tohoto striktního omezení vyloučíme pole s konstantním a statickým oprávněním jen pro čtení, protože taková pole, která jsou skoro podle definice, se nikdy nevyžadují ke změně.

 ❌Neposkytněte pole instance, která jsou veřejná nebo chráněná.

 Měli byste poskytnout vlastnosti pro přístup k polím místo jejich veřejné nebo chráněné.

 ✔️ použít konstantní pole pro konstanty, které se nikdy nezmění.

 Kompilátor vypálí hodnoty konstantních polí přímo na volání kódu. Proto hodnoty const nelze nikdy změnit bez rizika přerušení kompatibility.

 ✔️ použít veřejné statické `readonly` pole pro předdefinované instance objektů.

 Pokud existují předdefinované instance typu, deklarujte je jako veřejná pole pouze pro čtení samotného typu.

 ❌Nepřiřazujte do polí instance proměnlivých typů `readonly` .

 Proměnlivý typ je typ s instancemi, které lze změnit po vytvoření instance. Například pole, většina kolekcí a datové proudy jsou proměnlivé typy, ale <xref:System.Int32?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> a <xref:System.String?displayProperty=nameWithType> jsou všechny neměnné. Modifikátor jen pro čtení v poli typu odkazu brání instanci, která je uložena v poli, aby byla měněna, ale nezabrání v tom, aby byla data instance pole upravována voláním členů, kteří mění instanci.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny pro návrh členů](member.md)
- [Pokyny k návrhu architektury](index.md)
