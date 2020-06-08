---
title: 'Postupy: Povolení žádosti WebRequest, aby používal proxy server pro komunikaci s internetem'
description: Naučte se, jak vytvořit globální proxy instance, aby mohla kterákoli WebRequest používat proxy server ke komunikaci s internetem v .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 0fc33cea3f5a7fe4669b110e53e71afdb9561c23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502532"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="182d9-103">Postupy: Povolení žádosti WebRequest, aby používal proxy server pro komunikaci s internetem</span><span class="sxs-lookup"><span data-stu-id="182d9-103">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="182d9-104">Tento příklad vytvoří globální instanci proxy serveru, která umožní <xref:System.Net.WebRequest> použít proxy server ke komunikaci s internetem.</span><span class="sxs-lookup"><span data-stu-id="182d9-104">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="182d9-105">V příkladu se předpokládá, že proxy server má název `webproxy` a že komunikuje na portu 80 standardního portu HTTP.</span><span class="sxs-lookup"><span data-stu-id="182d9-105">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="182d9-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="182d9-106">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="182d9-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="182d9-107">Compiling the Code</span></span>

<span data-ttu-id="182d9-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="182d9-108">This example requires:</span></span>

- <span data-ttu-id="182d9-109">[ `using` Direktiva](../../csharp/language-reference/keywords/using-directive.md) jazyka C# pro obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="182d9-109">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="182d9-110">[ `Imports` Příkaz](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic pro obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="182d9-110">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="182d9-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="182d9-111">See also</span></span>

- [<span data-ttu-id="182d9-112">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="182d9-112">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="182d9-113">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="182d9-113">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
