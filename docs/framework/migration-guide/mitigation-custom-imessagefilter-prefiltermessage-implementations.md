---
title: 'Zmírnění: Vlastní implementace iMessageFilter.PreFilterMessageMessageMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400118"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Zmírnění: Vlastní implementace iMessageFilter.PreFilterMessageMessageMessage

V aplikacích pro Windows Forms, které cílí na verze rozhraní .NET Framework <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> počínaje rozhraním .NET Framework 4.6.1, může vlastní implementace bezpečně filtrovat zprávy při volání <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metody, pokud je <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace:

- Má jeden nebo oba z následujících:

  - Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.

  - Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody. Metoda.

- **A** pumpuje zprávy <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> voláním metody.

## <a name="impact"></a>Dopad

Tato změna ovlivní pouze aplikace pro Windows Forms, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.1.

Pro aplikace pro Windows Forms, které cílí na předchozí verze rozhraní <xref:System.IndexOutOfRangeException> .NET <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> Framework, tyto implementace v některých případech vyvolat výjimku při volání metody

## <a name="mitigation"></a>Omezení rizik

Pokud je tato změna nežádoucí, aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo [ \<](../configure-apps/file-schema/runtime/runtime-element.md) novější verzi, se z ní mohou odhlásit přidáním následujícího nastavení konfigurace do části runtime>konfiguračního souboru aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Kromě toho se aplikace, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rámci rozhraní .NET Framework [ \<](../configure-apps/file-schema/runtime/runtime-element.md) 4.6.1 nebo novější verze, mohou přihlásit k tomuto chování přidáním následujícího nastavení konfigurace do části konfigurace konfiguračního souboru aplikace>běhu:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
