---
title: 'Postupy: Konfigurace domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8989d7695f44b0cd2e8b0ce3ec8bd74a6e802102
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534563"
---
# <a name="how-to-configure-an-application-domain"></a>Postupy: Konfigurace domény aplikace
Modul common language runtime může poskytnout informace o konfiguraci pro novou doménu aplikace pomocí <xref:System.AppDomainSetup> třídy. Při vytváření vlastních domén aplikace, je nejdůležitější vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A>. Druhý **AppDomainSetup** vlastnosti jsou používány především hostitelská prostředí modulu runtime pro konfiguraci domény konkrétní aplikace.  
  
 **ApplicationBase** definuje vlastnost kořenový adresář aplikace. Když modul runtime je potřeba splnit žádost o typ, sondy pro sestavení obsahující typ v adresáři určeném argumentem **ApplicationBase** vlastnost.  
  
> [!NOTE]
>  Nová doména aplikace dědí pouze **ApplicationBase** vlastnosti Tvůrce.  
  
 Následující příklad vytvoří instance **AppDomainSetup** třídy, tato třída používá k vytvoření nové aplikační doméně, zapisuje tyto informace do konzoly a poté uvolní domény aplikace.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- [Programování pomocí domén aplikace](application-domains.md#programming-with-application-domains)
- [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
