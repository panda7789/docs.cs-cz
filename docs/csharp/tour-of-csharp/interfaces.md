---
title: C#Rozhraní – připravuje C# jazyka
description: Definování kontraktů implementovaných typů v rozhraníC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: bfc6b59a411ff2ddb3331a8bdf24c0ae3d611273
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144114"
---
# <a name="interfaces"></a>Rozhraní

***Rozhraní*** definuje kontrakt, který může být implementována třídy a struktury. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů definuje – pouze Určuje členy, které je třeba dodat ze třídy nebo struktury, které implementují rozhraní.

Rozhraní může využívat ***vícenásobná dědičnost***. V následujícím příkladu, rozhraní `IComboBox` zdědí vlastnosti z obou `ITextBox` a `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Třídy a struktury mohou implementovat více rozhraní. V následujícím příkladu třída `EditBox` implementuje oba `IControl` a `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Pokud konkrétní rozhraní implementuje, třídy nebo struktury, instance této třídy nebo struktury lze implicitně převést na tento typ rozhraní. Příklad

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

V případech, kde není instance znám staticky implementovat určité rozhraní je možné dynamického přetypování. Například následující příkazy použijte k získání objektu dynamického přetypování `IControl` a `IDataBound` implementace rozhraní. Protože je za běhu skutečný typ objektu `EditBox`, úspěšné položky CAST.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

V předchozím `EditBox` třídy, `Paint` metodu z `IControl` rozhraní a `Bind` metodu z `IDataBound` rozhraní jsou implementovány pomocí veřejné členy. C#také podporuje explicitní ***implementace členů rozhraní***, povolení dané třídy nebo struktury předejděte tomu, aby veřejné členy. Implementace explicitního rozhraní člen je zapsáno s použitím rozhraní plně kvalifikovaný název člena. Například `EditBox` třída může implementovat `IControl.Paint` a `IDataBound.Bind` metod pomocí explicitní implementace členů rozhraní následujícím způsobem.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Explicitní rozhraní členy jsou přístupné pouze prostřednictvím typu rozhraní. Například provádění `IControl.Paint` zadaný podle předchozí EditBox třídy lze vyvolat pouze první převedením `EditBox` odkaz `IControl` typu rozhraní.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Předchozí](arrays.md)
>[další](enums.md)