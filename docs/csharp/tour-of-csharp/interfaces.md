---
title: "Rozhraní jazyka C# – přehled používání jazyka C#"
description: "Rozhraní definovat kontrakty implementované typy v jazyku C#"
keywords: "Rozhraní .NET, csharp, rozhraní, vícenásobná dědičnost polymorfismus"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a>Rozhraní

***Rozhraní*** definuje kontrakt, který může být implementována třídy a struktury. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů definuje – jenom určuje členů, které je nutné zadat třídy nebo struktury, které implementují rozhraní.

Rozhraní mohou využívat ***vícenásobná dědičnost***. V následujícím příkladu, rozhraní `IComboBox` zdědí vlastnosti z obou `ITextBox` a `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Třídy a struktury můžete implementovat více rozhraní. V následujícím příkladu třída `EditBox` implementuje obě `IControl` a `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Při třídě nebo struktuře implementuje určité rozhraní, může instance této třídě nebo struktuře implicitně převést na tento typ rozhraní. Příklad

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

V případech, kde instance nezná staticky implementovat určité rozhraní můžete použít dynamický typ přetypování. Například následující příkazy použít dynamický typ přetypování k získání objektu `IControl` a `IDataBound` rozhraní implementace. Protože je skutečný typ spuštění objektu `EditBox`, položky CAST úspěšné.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

V předchozím `EditBox` třídy, `Paint` metoda z `IControl` rozhraní a `Bind` metoda z `IDataBound` rozhraní jsou implementované pomocí veřejné členy. C# také podporuje explicitní ***rozhraní implementace členských***, povolení třídě nebo struktuře vyhnout se provádění veřejné členy. Implementace explicitního rozhraní člen je vytvořené pomocí rozhraní plně kvalifikovaný název člena. Například `EditBox` třída může implementovat `IControl.Paint` a `IDataBound.Bind` metod pomocí explicitní rozhraní implementace členských následujícím způsobem.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Členové explicitní rozhraní jsou přístupné pouze prostřednictvím typu rozhraní. Například implementace `IControl.Paint` zadaný podle předchozích textového pole třídu jde volat jenom první převedením `EditBox` odkaz na `IControl` typ rozhraní.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
[Předchozí](arrays.md)
[další](enums.md)
