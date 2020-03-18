---
title: Delegáti jazyka C# – prohlídka jazyka C#
description: Naučte se pozdní vazbu s delegáty Jazyka C#
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159166"
---
# <a name="delegates"></a>Delegáty

***Typ delegáta*** představuje odkazy na metody s určitým seznamem parametrů a návratovým typem. Delegáti umožňují považovat metody za entity, které lze přiřadit proměnným a předat jako parametry. Delegáti jsou podobné konceptu ukazatelů funkce v některých jiných jazycích. Na rozdíl od ukazatelů funkce jsou delegáti objektově orientovaní a typově bezpeční.

Následující příklad deklaruje a `Function`používá typ delegáta s názvem .

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Instance typu `Function` delegáta může odkazovat na `double` libovolnou `double` metodu, která přebírá argument a vrací hodnotu. Metoda `Apply` použije danou funkci na prvky `double[]`, vracející `double[]` se s výsledky. V `Main` metodě `Apply` se používá použít tři `double[]`různé funkce .

Delegát může odkazovat na statickou `Square` `Math.Sin` metodu (například nebo v předchozím `m.Multiply` příkladu) nebo metodu instance (například v předchozím příkladu). Delegát, který odkazuje na metodu instance, také odkazuje na určitý objekt a při vyvolání metody instance prostřednictvím delegáta se tento objekt stane `this` vyvoláním.

Delegáti mohou být také vytvořeny pomocí anonymních funkcí, které jsou "vsazené metody", které jsou vytvořeny při deklarování. Anonymní funkce mohou zobrazit místní proměnné okolních metod. Následující příklad nevytváří třídu:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Delegát neví, nebo péče o třídu metody, na kterou odkazuje; vše, na čem záleží, je, že odkazovaná metoda má stejné parametry a návratový typ jako delegát.

>[!div class="step-by-step"]
>[Předchozí](interfaces.md)
>[další](attributes.md)
