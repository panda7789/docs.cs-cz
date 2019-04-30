---
title: 'Omezení rizik: Custom IMessageFilter.PreFilterMessage Implementations'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4faf42d3be4f76e5908068b1c2f88d7803ae18df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871550"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Omezení rizik: Custom IMessageFilter.PreFilterMessage Implementations

V aplikacích Windows Forms, které se zaměřují rozhraní .NET Framework počínaje verzí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace může bezpečně filtru zprávy, když <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda je volána, pokud <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace:

- Provede jednu nebo obě z následujících akcí:

  - Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.

  - Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody. Metoda.

- **A** čerpadla zprávy voláním <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.

## <a name="impact"></a>Dopad

Tato změna ovlivní pouze aplikace Windows Forms, které se zaměřují rozhraní .NET Framework počínaje verzí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].

Pro aplikace Windows Forms, které cílí na předchozí verze rozhraní .NET Framework, vyvolá tato implementace v některých případech <xref:System.IndexOutOfRangeException> výjimka při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání metody

## <a name="mitigation"></a>Zmírnění

Pokud tuto změnu nežádoucí, aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nebo novější můžete vyjádřit výslovný nesouhlas ho tak, že přidáte následující konfigurační nastavení [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

Kromě toho, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nebo novější můžete přejít k tomuto chování tak, že přidáte následující konfigurační nastavení pro [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)oddílu konfiguračního souboru aplikace:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
