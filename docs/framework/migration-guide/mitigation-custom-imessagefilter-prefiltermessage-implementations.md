---
title: 'Zmírnění: vlastní implementace IMessageFilter. PreFilterMessage'
description: Přečtěte si o vlastních IMessageFilter. PreFilterMessage implementaci obsažených v aplikacích model Windows Forms, které cílí na .NET Framework 4.6.1 a novějších.
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475252"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Zmírnění: vlastní implementace IMessageFilter. PreFilterMessage

V model Windows Forms aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> může vlastní implementace bezpečně filtrovat zprávy při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání metody, pokud <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace:

- Provede jednu nebo obě následující akce:

  - Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.

  - Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody. Metoda.

- **A** zprávy pumpy voláním <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.

## <a name="impact"></a>Dopad

Tato změna má vliv pouze na aplikace model Windows Forms, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.

Pro model Windows Forms aplikace cílené na předchozí verze .NET Framework taková implementace v některých případech vyvolá <xref:System.IndexOutOfRangeException> výjimku při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání metody.

## <a name="mitigation"></a>Omezení rizik

Pokud je tato změna nežádoucí, můžou se aplikace, které cílí na .NET Framework 4.6.1 nebo novější verze, odhlásit, a to přidáním následujícího nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 nebo novější verzi, se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
