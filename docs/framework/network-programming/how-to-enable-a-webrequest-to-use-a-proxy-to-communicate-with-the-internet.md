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
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Postupy: Povolení žádosti WebRequest, aby používal proxy server pro komunikaci s internetem

Tento příklad vytvoří globální proxy instanci, která umožní jakékoli <xref:System.Net.WebRequest> použití proxy ke komunikaci s Internetem. Příklad předpokládá, že proxy server `webproxy` je pojmenován a že komunikuje na portu 80, standardním portu HTTP.

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

- [ `using` Direktiva](../../csharp/language-reference/keywords/using-directive.md) Jazyka **C#** pro System.Net oboru názvů.
- Příkaz jazyka Visual [ `Imports` Basic](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro **System.Net** oboru názvů.

## <a name="see-also"></a>Viz také

- [Použití aplikačních protokolů](using-application-protocols.md)
- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
