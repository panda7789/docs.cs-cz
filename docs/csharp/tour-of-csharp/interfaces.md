---
title: Rozhraní Jazyka C# – prohlídka jazyka C#
description: 'Rozhraní definují smlouvy implementované typy v C #'
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159127"
---
# <a name="interfaces"></a>Rozhraní

***Rozhraní*** definuje smlouvu, která může být implementována třídami a strukturami. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů, které definuje – pouze určuje členy, které musí být dodány třídy nebo struktury, které implementují rozhraní.

Rozhraní mohou využívat ***více dědičnosti***. V následujícím příkladu `IComboBox` rozhraní dědí `ITextBox` `IListBox`z obou a .

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Třídy a struktury mohou implementovat více rozhraní. V následujícím příkladu `EditBox` třída implementuje oba `IControl` a `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Když třída nebo struktura implementuje určité rozhraní, instance této třídy nebo struktury lze implicitně převést na tento typ rozhraní. Například

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

V případech, kdy instance není staticky známo, že implementovat určité rozhraní, dynamický typ přetypovádá lze použít. Například následující příkazy používají přetypové dynamické typy `IControl` `IDataBound` k získání implementace objektu a rozhraní. Vzhledem k tomu, že skutečný `EditBox`typ objektu za běhu je , přetypová tažné období úspěšné.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

V předchozí `EditBox` třídě `Paint` metoda z `IControl` rozhraní `Bind` a metoda `IDataBound` z rozhraní jsou implementovány pomocí veřejné členy. C# také podporuje explicitní implementace členů rozhraní , povolení ***třídy***nebo struktury, aby se zabránilo vytváření členů veřejnosti. Explicitní implementace člena rozhraní je zapsána pomocí plně kvalifikovaného názvu člena rozhraní. Například `EditBox` třída může implementovat `IControl.Paint` a `IDataBound.Bind` metody pomocí explicitní implementace členů rozhraní takto.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Explicitní členové rozhraní lze přistupovat pouze prostřednictvím typu rozhraní. Například implementaci `IControl.Paint` poskytuje předchozí EditBox třídy lze vyvolat pouze nejprve `EditBox` převést `IControl` odkaz na typ rozhraní.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Předchozí](arrays.md)
>[další](delegates.md)
