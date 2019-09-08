---
title: Zmírnění Vlastní implementace IMessageFilter. PreFilterMessage
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af81468c5c4c4caf2f09725d6c7c4723084e35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779429"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Zmírnění Vlastní implementace IMessageFilter. PreFilterMessage

V model Windows Forms aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, může vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace bezpečně filtrovat zprávy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> při volání <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> metody, pokud implementace:

- Provede jednu nebo obě následující akce:

  - Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.

  - Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody. Metoda.

- **A** zprávy pumpy voláním <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.

## <a name="impact"></a>Dopad

Tato změna má vliv pouze na aplikace model Windows Forms, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.

Pro model Windows Forms aplikace cílené na předchozí verze .NET Framework taková implementace v některých případech vyvolá <xref:System.IndexOutOfRangeException> výjimku <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> při volání metody.

## <a name="mitigation"></a>Zmírnění

Pokud je tato změna nežádoucí, můžou se aplikace, které cílí na .NET Framework 4.6.1 nebo novější verze, odhlásit, a to přidáním následujícího nastavení konfigurace do [ \<části > modulu runtime](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale jsou spuštěné v .NET Framework 4.6.1 nebo novější verzi, se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do [ \<části běhového prostředí >](../configure-apps/file-schema/runtime/runtime-element.md) konfigurační soubor aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6-1.md)
