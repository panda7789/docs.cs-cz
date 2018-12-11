---
title: C#Delegáti – připravuje C# jazyka
description: Přečtěte si pozdní vazbu s C# delegátů
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 2744f774392ef021974535de535b063264ae9a54
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151275"
---
# <a name="delegates"></a>Delegáty

A ***typ delegáta*** seznamu představuje odkazy na metody pomocí konkrétních parametrů a návratový typ. Delegáty umožňují považovat za entity, které může být přiřazena k proměnné a předány jako parametry metod. Delegáti jsou podobný koncept ukazatelů na funkce v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, Delegáti jsou objektově orientované a typově bezpečné.

Následující příklad deklaruje a používá typ delegáta s názvem `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Instance `Function` typ delegáta může odkazovat na jakoukoli metodu, která přijímá `double` argument a vrátí `double` hodnotu. `Apply` Metoda použije danou funkci na elementy `double[]`, vrácení `double[]` s výsledky. V `Main` metody `Apply` slouží k použití tří různých funkcí `double[]`.

Delegát může odkazovat na statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu) nebo metodu instance (například `m.Multiply` v předchozím příkladu). Delegát, který odkazuje na metodu instance také odkazuje na konkrétní objekt, a když uživatel vyvolá metodu instance prostřednictvím delegáta, tento objekt se stane `this` ve volání.

Delegáty lze vytvořit také pomocí anonymní funkce, které jsou "inline metod", které jsou vytvořeny v reálném čase. Anonymní funkce můžete zobrazit místní proměnné okolního metody. Díky tomu se výše uvedený příklad multiplikátor může být zapsán snadněji bez použití multiplikátor třídy:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Zajímavé a užitečné vlastnictví delegáta je, že ho neznáte nebo postaral o třídě, na které odkazuje; metody vše, co je důležité je, že odkazované metody má stejné parametry a návratový typ jako delegát.

>[!div class="step-by-step"]
>[Předchozí](enums.md)
>[další](attributes.md)