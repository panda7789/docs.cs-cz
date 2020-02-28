---
title: C#Delegáti – prohlídka C# jazyka
description: Přečtěte si pozdní C# vazbu s delegáty
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159166"
---
# <a name="delegates"></a>Delegáty

***Typ delegáta*** představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry. Delegáti jsou podobní pojmu ukazatelů na funkce nalezených v některých jiných jazycích. Na rozdíl od ukazatelů na funkce jsou delegáti objektově orientovaný a typově bezpečný.

Následující příklad deklaruje a používá typ delegáta s názvem `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Instance typu delegáta `Function` může odkazovat na jakoukoli metodu, která přebírá `double` argument a vrací hodnotu `double`. Metoda `Apply` použije danou funkci na prvky `double[]`a vrátí `double[]` s výsledky. V metodě `Main` se `Apply` používá k použití tří různých funkcí na `double[]`.

Delegát může odkazovat buď na statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu), nebo na metodu instance (například `m.Multiply` v předchozím příkladu). Delegát, který odkazuje na metodu instance, také odkazuje na konkrétní objekt a když je metoda instance vyvolána prostřednictvím delegáta, objekt se ve vyvolání `this`.

Delegáty lze také vytvořit pomocí anonymních funkcí, což jsou "vložené metody", které jsou vytvořeny při deklaraci. Anonymní funkce mohou zobrazit místní proměnné okolních metod. Následující příklad nevytvoří třídu:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Delegát neví ani nezáleží na třídě metody, na kterou odkazuje; všechny tyto věci jsou, že odkazovaná metoda má stejné parametry a návratový typ jako delegát.

>[!div class="step-by-step"]
>[Předchozí](interfaces.md)
>[Další](attributes.md)
