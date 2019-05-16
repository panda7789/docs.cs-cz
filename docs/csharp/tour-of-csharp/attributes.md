---
title: C# atributy – prohlídka jazyka C#
description: Další informace o deklarativní programování v jazyce C# pomocí atributů
ms.date: 08/10/2016
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 79bd14ebd3b25eabc0b9f7ed8f9e9585a050805f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634643"
---
# <a name="attributes"></a>Atributy

Typy, členy a dalších entit v programu v jazyce C# podporují modifikátory, které ovládat některé aspekty jejich chování. Například pro usnadnění metody je řízen pomocí `public`, `protected`, `internal`, a `private` modifikátory. C# umožňuje zobecnit tuto funkci tak, uživatelem definované typy deklarativní informací můžete připojit k programu entity a načíst v době běhu. Programy zadejte tyto dodatečné informace deklarativní definice a používání ***atributy***.

Následující příklad deklaruje `HelpAttribute` atribut, který může být umístěn v programu entity, které obsahují odkazy na jejich související dokumentaci.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Všechny třídy atributu odvozovat <xref:System.Attribute> základní třídy, které jsou k dispozici ve standardní knihovně. Atributy lze použít zadáním jeho názvu, spolu s žádné argumenty, v hranatých závorkách těsně před deklaraci přidružené. Pokud název atributu končí na `Attribute`, část názvu lze vynechat, pokud se odkazuje atribut. Například `HelpAttribute` je možné následujícím způsobem.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Tento příklad připojí `HelpAttribute` k `Widget` třídy. Přidá další `HelpAttribute` k `Display` metody ve třídě. Veřejné konstruktory třídu atributu řídit informace, které musí být zadaná, když je připojena k entitě programu. Další informace lze zadat pomocí odkazu na veřejné čtení a zápis vlastnosti třídy atributů (jako je například odkaz na `Topic` vlastnost dříve).

Metadata definované atributy může číst a zpracovat za běhu pomocí operace reflection. Když konkrétní atribut je požadovaný touto technikou, konstruktor pro třídu atributu je vyvolán pomocí informací uvedených ve zdrojovém programu a vrátí se výsledná instance atributu. Pokud Další informace se poskytovaly prostřednictvím vlastností, tyto vlastnosti jsou nastavené na dané hodnoty před vrácením instance atributu.

Následující příklad kódu ukazuje, jak získat `HelpAttribute` instance přidružené k `Widget` třídy a jeho `Display` metoda.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
>[Předchozí](delegates.md)
