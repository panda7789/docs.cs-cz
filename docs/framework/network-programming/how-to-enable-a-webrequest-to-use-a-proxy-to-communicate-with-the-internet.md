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
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Postupy: Povolení žádosti WebRequest, aby používal proxy server pro komunikaci s internetem

Tento příklad vytvoří globální instanci proxy serveru, která umožní <xref:System.Net.WebRequest> použít proxy server ke komunikaci s internetem. V příkladu se předpokládá, že proxy server má název `webproxy` a že komunikuje na portu 80 standardního portu HTTP.

## <a name="example"></a>Příklad

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

- [ `using` Direktiva](../../csharp/language-reference/keywords/using-directive.md) jazyka C# pro obor názvů **System.NET** .
- [ `Imports` Příkaz](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic pro obor názvů **System.NET** .

## <a name="see-also"></a>Viz také:

- [Použití aplikačních protokolů](using-application-protocols.md)
- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
