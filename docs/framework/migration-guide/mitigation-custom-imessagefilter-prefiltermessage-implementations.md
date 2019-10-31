---
title: 'Zmírnění: vlastní implementace IMessageFilter. PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5174c67e4204c2e20e5730ab7c092ccbb0aeda1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126267"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Zmírnění: vlastní implementace IMessageFilter. PreFilterMessage

V aplikaci model Windows Forms aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, vlastní implementace <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> může bezpečně filtrovat zprávy, když je metoda <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volána, pokud <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace:

- Provede jednu nebo obě následující akce:

  - Přidá filtr zpráv voláním metody <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.

  - Odebere filtr zpráv voláním metody <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. Metoda.

- **A** zprávy pumpy voláním metody <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.

## <a name="impact"></a>Dopad

Tato změna má vliv pouze na aplikace model Windows Forms, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.

Pro model Windows Forms aplikace, které cílí na předchozí verze .NET Framework, takové implementace v některých případech vyvolají výjimku <xref:System.IndexOutOfRangeException> při volání metody <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

## <a name="mitigation"></a>Zmírnění

Pokud je tato změna nežádoucí, můžou se aplikace, které cílí na .NET Framework 4.6.1 nebo novější verze, odhlásit přidáním následujícího nastavení konfigurace do části [\<modulu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 nebo novější verzi, se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do části [> modulu runtime\<](../configure-apps/file-schema/runtime/runtime-element.md) konfigurační soubor aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6-1.md)
