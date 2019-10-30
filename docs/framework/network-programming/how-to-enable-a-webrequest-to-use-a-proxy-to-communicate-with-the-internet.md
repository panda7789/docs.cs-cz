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
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Postupy: povolení služby WebRequest k použití proxy serveru ke komunikaci s internetem

Tento příklad vytvoří globální instanci proxy serveru, která umožní, aby <xref:System.Net.WebRequest> používat proxy server ke komunikaci s internetem. V příkladu se předpokládá, že proxy server má název `webproxy` a že komunikuje na portu 80 standardního portu HTTP.

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

- C# [Direktiva`using`](../../csharp/language-reference/keywords/using-directive.md) pro obor názvů **System.NET** .
- Příkaz Visual Basic [`Imports`](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro obor názvů **System.NET** .

## <a name="see-also"></a>Viz také:

- [Použití aplikačních protokolů](using-application-protocols.md)
- [Přístup k internetu přes proxy server](accessing-the-internet-through-a-proxy.md)
