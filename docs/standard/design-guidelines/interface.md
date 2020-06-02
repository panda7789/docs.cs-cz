---
title: Návrh rozhraní
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: f589d47d5b945179430275598996b2fb77e92848
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289028"
---
# <a name="interface-design"></a>Návrh rozhraní
I když je většina rozhraní API nejlépe modelována pomocí tříd a struktur, existují případy, kdy jsou rozhraní lépe vhodná, nebo jenom možnost.

 CLR nepodporuje vícenásobnou dědičnost (tj. třídy CLR nemůžou dědit z více než jedné základní třídy), ale umožňuje typům implementovat jednu nebo více rozhraní kromě dědění ze základní třídy. Rozhraní se proto často používají k dosažení účinku vícenásobné dědičnosti. Například <xref:System.IDisposable> je rozhraní, které umožňuje typům podporovat disposability nezávisle na jakékoli jiné hierarchii dědičnosti, v níž se chtějí zúčastnit.

 Další situací, ve které je definování rozhraní vhodné, je vytvoření společného rozhraní, které může být podporováno několika typy, včetně některých typů hodnot. Typy hodnot nemůžou dědit z jiných typů než <xref:System.ValueType> , ale můžou implementovat rozhraní, takže použití rozhraní je jedinou možností, aby se mohl poskytnout společný základní typ.

 ✔️ definovat rozhraní, pokud potřebujete některé společné rozhraní API podporovat sadou typů, které obsahují typy hodnot.

 ✔️ Zvažte definování rozhraní, pokud potřebujete podporovat jeho funkci u typů, které již dědí z jiného typu.

 ❌Vyhněte se použití rozhraní značek (rozhraní bez členů).

 Pokud potřebujete označit třídu jako se specifickou charakteristikou (marker), použijte obecně vlastní atribut, nikoli rozhraní.

 ✔️ Zadejte alespoň jeden typ, který je implementací rozhraní.

 To pomáhá ověřit návrh rozhraní. Například <xref:System.Collections.Generic.List%601> je implementací <xref:System.Collections.Generic.IList%601> rozhraní.

 ✔️ Zadejte alespoň jedno rozhraní API, které využívá každé rozhraní, které definujete (metodu přebírající rozhraní jako parametr nebo vlastnost typu jako rozhraní).

 To pomáhá ověřit návrh rozhraní. Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> používá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> rozhraní.

 ❌Nepřidávat členy do rozhraní, které bylo dříve expedováno.

 Tím by došlo k přerušení implementace rozhraní. Aby nedocházelo k problémům se správou verzí, měli byste vytvořit nové rozhraní.

 S výjimkou případů popsaných v těchto pokynech byste měli obecně zvolit třídy namísto rozhraní v návrhu opakovaně použitelných knihoven spravovaného kódu.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny pro návrh typů](type.md)
- [Pokyny k návrhu architektury](index.md)
