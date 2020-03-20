---
title: 'Postupy: Povolení žádosti WebRequest, aby používal proxy server pro komunikaci s internetem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039542"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="99e6a-102">Postupy: Povolení žádosti WebRequest, aby používal proxy server pro komunikaci s internetem</span><span class="sxs-lookup"><span data-stu-id="99e6a-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="99e6a-103">Tento příklad vytvoří globální proxy instanci, která umožní jakékoli <xref:System.Net.WebRequest> použití proxy ke komunikaci s Internetem.</span><span class="sxs-lookup"><span data-stu-id="99e6a-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="99e6a-104">Příklad předpokládá, že proxy server `webproxy` je pojmenován a že komunikuje na portu 80, standardním portu HTTP.</span><span class="sxs-lookup"><span data-stu-id="99e6a-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="99e6a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="99e6a-105">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="99e6a-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="99e6a-106">Compiling the Code</span></span>

<span data-ttu-id="99e6a-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="99e6a-107">This example requires:</span></span>

- <span data-ttu-id="99e6a-108">[ `using` Direktiva](../../csharp/language-reference/keywords/using-directive.md) Jazyka **C#** pro System.Net oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="99e6a-108">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="99e6a-109">Příkaz jazyka Visual [ `Imports` Basic](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="99e6a-109">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="99e6a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="99e6a-110">See also</span></span>

- [<span data-ttu-id="99e6a-111">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="99e6a-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="99e6a-112">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="99e6a-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
