---
title: C#Rozhraní – prohlídka C# jazyka
description: Rozhraní definují smlouvy implementované typy vC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: d10d9f69cebe9a05cdff9b9ff5d817237bf8c56f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346831"
---
# <a name="interfaces"></a>Rozhraní

***Rozhraní*** definuje kontrakt, který může být implementován pomocí tříd a struktur. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní neposkytuje implementace členů, které definuje – určuje pouze členy, které musí být poskytnuty třídami nebo strukturami, které implementují rozhraní.

Rozhraní mohou využívat ***vícenásobnou dědičnost***. V následujícím příkladu rozhraní `IComboBox` dědí z `ITextBox` a `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Třídy a struktury mohou implementovat více rozhraní. V následujícím příkladu třída `EditBox` implementuje `IControl` a `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Pokud třída nebo struktura implementuje konkrétní rozhraní, instance této třídy nebo struktury lze implicitně převést na tento typ rozhraní. Příklad

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

V případech, kdy instance není staticky známá pro implementaci konkrétního rozhraní, lze použít dynamické přetypování typu. Například následující příkazy používají přetypování dynamického typu k získání `IControl` a `IDataBound` rozhraní objektu. Vzhledem k tomu, že je skutečný typ objektu run-time `EditBox`, přetypování je úspěšné.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

V předchozí třídě `EditBox` jsou implementovány `Paint` metoda z rozhraní `IControl` a metoda `Bind` z rozhraní `IDataBound` pomocí veřejných členů. C#podporuje také explicitní ***implementace členů rozhraní***, což umožňuje třídě nebo struktuře zabránit členům Public. Explicitní implementace člena rozhraní je zapsána pomocí plně kvalifikovaného názvu člena rozhraní. Například třída `EditBox` by mohla implementovat metody `IControl.Paint` a `IDataBound.Bind` pomocí explicitních implementací členů rozhraní následujícím způsobem.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

K explicitním členům rozhraní lze přistupovat pouze prostřednictvím typu rozhraní. Například implementace `IControl.Paint` poskytovaná předchozí třídou EditBox lze vyvolat pouze první převod `EditBox` odkaz na typ rozhraní `IControl`.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Předchozí](arrays.md)
>[Další](delegates.md)
