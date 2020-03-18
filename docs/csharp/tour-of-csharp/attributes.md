---
title: C# Atributy - prohlídka jazyka C#
description: 'Informace o deklarativním programování pomocí atributů v jazyce C #'
ms.date: 02/27/2020
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: dc5b194c22fc2746ff8b0ab3e550e560a3666bbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159205"
---
# <a name="attributes"></a>Atributy

Typy, členy a další entity v programu jazyka C# podporují modifikátory, které řídí určité aspekty jejich chování. Například přístupnost metody je řízena `public` `protected`pomocí `internal`modifikátorů , a `private` modifikátorů . C# generalizuje tuto schopnost tak, aby uživatelem definované typy deklarativní informace mohou být připojeny k entitám programu a načteny za běhu. Programy určují tyto další deklarativní informace definováním a použitím ***atributů***.

Následující příklad deklaruje `HelpAttribute` atribut, který lze umístit na entity programu a poskytnout odkazy na jejich přidruženou dokumentaci.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Všechny třídy atributů jsou odvozeny <xref:System.Attribute> ze základní třídy poskytované standardní knihovnou. Atributy lze použít tím, že jejich název, spolu s argumenty, uvnitř hranatých závorek těsně před přidružené deklarace. Pokud název atributu končí `Attribute`na , může být tato část názvu vynechána, když je atribut odkazován. Například `HelpAttribute` lze použít následujícím způsobem.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Tento příklad připojí `HelpAttribute` a `Widget` ke třídě. Přidá další `HelpAttribute` k `Display` metodě ve třídě. Veřejné konstruktory třídy atributů řídí informace, které musí být poskytnuty, když je atribut připojen k entitě programu. Další informace lze poskytnout odkazem na veřejné vlastnosti čtení a zápisu `Topic` třídy atributu (například odkaz na vlastnost dříve).

Metadata definovaná atributy lze číst a manipulovat za běhu pomocí reflexe. Pokud je pomocí této techniky požadován určitý atribut, je konstruktor pro třídu atributu vyvolán s informacemi poskytnutými ve zdroji programu a je vrácena výsledná instance atributu. Pokud byly poskytnuty další informace prostřednictvím vlastností, tyto vlastnosti jsou nastaveny na dané hodnoty před vrácením instance atributu.

Následující ukázka kódu ukazuje, `HelpAttribute` jak získat instance `Widget` přidružené `Display` ke třídě a její metodě.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
>[Předchozí](delegates.md)
