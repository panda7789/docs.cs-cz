---
title: C#Delegáti – prohlídka C# jazyka
description: Přečtěte si pozdní C# vazbu s delegáty
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 317d3ee6fb1350824fa9b3b4d0e3e851780ce4d4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346868"
---
# <a name="delegates"></a>Delegáti

***Typ delegáta*** představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou podobní pojmu ukazatelů na funkce nalezené v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce jsou delegáti objektově orientované a typově bezpečné.

Následující příklad deklaruje a používá typ delegáta s názvem `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Instance typu delegáta `Function` může odkazovat na jakoukoli metodu, která přebírá `double` argument a vrací hodnotu `double`. Metoda `Apply` použije danou funkci na prvky `double[]`a vrátí `double[]` s výsledky. V metodě `Main` se `Apply` používá k použití tří různých funkcí na `double[]`.

Delegát může odkazovat buď na statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu), nebo na metodu instance (například `m.Multiply` v předchozím příkladu). Delegát, který odkazuje na metodu instance, také odkazuje na konkrétní objekt a když je metoda instance vyvolána prostřednictvím delegáta, objekt se ve vyvolání `this`.

Delegáty je také možné vytvořit pomocí anonymních funkcí, což jsou "vložené metody", které jsou vytvářeny průběžně. Anonymní funkce mohou zobrazit místní proměnné okolních metod. Proto je příklad násobitele výše možné napsat snadněji bez použití třídy násobitele:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Zajímavou a užitečnou vlastností delegáta je, že neznají ani nezáleží na třídě metody, na kterou odkazuje; všechny tyto věci jsou, že odkazovaná metoda má stejné parametry a návratový typ jako delegát.

>[!div class="step-by-step"]
>[Předchozí](interfaces.md)
>[Další](attributes.md)
