---
title: 'Postupy: povolení služby WebRequest k použití proxy serveru ke komunikaci s internetem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039542"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="51d6d-102">Postupy: povolení služby WebRequest k použití proxy serveru ke komunikaci s internetem</span><span class="sxs-lookup"><span data-stu-id="51d6d-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="51d6d-103">Tento příklad vytvoří globální instanci proxy serveru, která umožní, aby <xref:System.Net.WebRequest> používat proxy server ke komunikaci s internetem.</span><span class="sxs-lookup"><span data-stu-id="51d6d-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="51d6d-104">V příkladu se předpokládá, že proxy server má název `webproxy` a že komunikuje na portu 80 standardního portu HTTP.</span><span class="sxs-lookup"><span data-stu-id="51d6d-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="51d6d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="51d6d-105">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="51d6d-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="51d6d-106">Compiling the Code</span></span>

<span data-ttu-id="51d6d-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="51d6d-107">This example requires:</span></span>

- <span data-ttu-id="51d6d-108">C# [Direktiva`using`](../../csharp/language-reference/keywords/using-directive.md) pro obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="51d6d-108">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="51d6d-109">Příkaz Visual Basic [`Imports`](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="51d6d-109">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="51d6d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51d6d-110">See also</span></span>

- [<span data-ttu-id="51d6d-111">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="51d6d-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="51d6d-112">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="51d6d-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
