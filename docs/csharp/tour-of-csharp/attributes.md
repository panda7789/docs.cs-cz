---
title: C#Atributy – prohlídka C# jazyka
description: Další informace o deklarativním programování pomocí atributů vC#
ms.date: 02/27/2020
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: dc5b194c22fc2746ff8b0ab3e550e560a3666bbe
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159205"
---
# <a name="attributes"></a>Atributy

Typy, členy a další entity v C# programu podporují modifikátory, které řídí určité aspekty jejich chování. Například přístupnost metody je řízena pomocí modifikátorů `public`, `protected`, `internal`a `private`. C#generalizuje tuto funkci tak, aby uživatelsky definované typy deklarativních informací mohly být připojeny k programovým entitám a načteny v době běhu. Programy určují tyto dodatečné deklarativní informace definováním a použitím ***atributů***.

Následující příklad deklaruje atribut `HelpAttribute`, který lze umístit do entit programu, aby poskytoval odkazy na jeho přidruženou dokumentaci.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Všechny třídy atributů jsou odvozeny od <xref:System.Attribute> základní třídy poskytované standardní knihovnou. Atributy lze použít zadáním jejich názvu spolu s případnými argumenty uvnitř hranatých závorek těsně před přidruženou deklarací. Pokud název atributu končí v `Attribute`, Tato část názvu může být vynechána při odkazování na atribut. `HelpAttribute` lze například použít následujícím způsobem.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Tento příklad připojí `HelpAttribute` ke třídě `Widget`. Přidá další `HelpAttribute` do metody `Display` ve třídě. Veřejné konstruktory třídy atributu určují informace, které je nutné zadat při připojení atributu k entitě programu. Další informace lze poskytnout odkazem na veřejné vlastnosti pro čtení a zápis třídy atributu (například odkaz na vlastnost `Topic` dříve).

Metadata definovaná atributy lze číst a manipulovat za běhu pomocí reflexe. Pokud je požadován konkrétní atribut pomocí této techniky, konstruktor třídy atributu je vyvolán s informacemi poskytnutými ve zdroji programu a výslednou instancí atributu je vrácen. Pokud byly k dispozici další informace prostřednictvím vlastností, jsou tyto vlastnosti nastaveny na zadané hodnoty před vrácením instance atributu.

Následující příklad kódu ukazuje, jak získat instance `HelpAttribute` přidružené ke třídě `Widget` a její `Display` metodou.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
>[Předchozí](delegates.md)
