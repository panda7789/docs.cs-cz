---
title: Nezapečetěné třídy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743563"
---
# <a name="unsealed-classes"></a>Nezapečetěné třídy
Zapečetěné třídy nelze dědit z a znemožňují rozšiřitelnost. Naopak třídy, které lze zdědit z, se nazývají nezapečetěné třídy.

 ✔️ Zvažte použití nezapečetěných tříd bez přidaných virtuálních nebo chráněných členů jako skvělý způsob, jak poskytnout nenákladnou rozšiřitelnost rozhraní.

 Vývojáři často chtějí zdědit z nezapečetěných tříd, aby mohli přidat praktické členy, jako jsou vlastní konstruktory, nové metody nebo přetížení metod. Například `System.Messaging.MessageQueue` není zapečetěný, takže umožní uživatelům vytvářet vlastní fronty, které jsou ve výchozím nastavení pro konkrétní cestu fronty, nebo přidat vlastní metody, které zjednodušují rozhraní API pro konkrétní scénáře.

 Třídy jsou ve výchozím nastavení ve většině programovacích jazyků nezapečetěné a toto je také Doporučená výchozí hodnota pro většinu tříd v rozhraních. Rozšiřitelnost, kterou poskytují nezapečetěné typy, je mnohem vážíme od uživatelů rozhraní a poměrně levného, aby poskytovala z důvodu relativně nízkých nákladů na testování spojených s nezapečetěnými typy.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Zapečetění](../../../docs/standard/design-guidelines/sealing.md)
