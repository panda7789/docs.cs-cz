---
title: "C# delegáti - přehled používání jazyka C#"
description: "Další informace pozdní vazba s C# delegáti"
keywords: "Rozhraní .NET, csharp, delegáta, lambda, pozdní vazba"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: bb304b2e5c762a44aab931b5e8f7fe9c99805eba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a>Delegáty

A ***delegovat typ*** seznamu představuje odkazy na metody s konkrétní parametr a návratovým typem. Delegáti umožňují považovat za entit, které může být přiřazena k proměnné a předány jako parametry metody. Delegáti jsou podobná koncept ukazatelů na funkce najít v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, jsou delegáti objektově orientované a bezpečnost typů.

Následující příklad deklaruje a používá typ delegáta s názvem `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Instance `Function` typ delegáta může odkazovat všechny metody, která přijímá `double` argument a vrátí `double` hodnotu. `Apply` Metoda platí pro elementy danou funkci `double[]`, vracejících `double[]` s výsledky. V `Main` metody `Apply` se používá k aplikování tři různé funkce `double[]`.

Delegáta může odkazovat buď statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu) nebo metodu instance (například `m.Multiply` v předchozím příkladu). Delegát, který odkazuje na metodu instance také odkazuje na konkrétní objekt, a když prostřednictvím delegáta je volána metoda instance, stane se tento objekt `this` v volání.

Delegáti lze vytvořit také pomocí anonymní funkce, které jsou "vložené metody", které jsou vytvořené za chodu. Anonymní funkce můžete zobrazit místní proměnné okolního metody. Proto je možné v předchozím příkladu násobitel zapsat snadněji bez použití třídy násobitel:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Podle zajímavé a užitečné vlastnosti delegáta je, že ho není vědět, nebo jsou pro vás o třídě metody, na které odkazuje; všechno, co záleží je, že má metodu odkazované stejnými parametry a návratový typ jako delegát.

>[!div class="step-by-step"]
[Předchozí](enums.md)
[další](attributes.md)
