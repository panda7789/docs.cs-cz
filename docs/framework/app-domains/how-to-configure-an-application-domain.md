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
ms.openlocfilehash: 06883646982aa6bd642dc4fce7881a289dad5901
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053195"
---
# <a name="how-to-configure-an-application-domain"></a>Postupy: Konfigurace domény aplikace
Modul CLR (Common Language Runtime) můžete zadat s informacemi o konfiguraci pro novou doménu aplikace <xref:System.AppDomainSetup> pomocí třídy. Při vytváření vlastních aplikačních domén je <xref:System.AppDomainSetup.ApplicationBase%2A>nejdůležitější vlastností. Další vlastnosti **AppDomainSetup** jsou používány převážně hostiteli modulu runtime ke konfiguraci konkrétní domény aplikace.  
  
 Vlastnost **ApplicationBase** definuje kořenový adresář aplikace. Pokud modul runtime potřebuje, aby splňoval požadavek typu, vyhledá sestavení obsahující typ v adresáři určeném vlastností **ApplicationBase** .  
  
> [!NOTE]
> Nová aplikační doména dědí pouze vlastnost **ApplicationBase** tvůrce.  
  
 Následující příklad vytvoří instanci třídy **AppDomainSetup** , používá tuto třídu k vytvoření nové domény aplikace, zapisuje informace do konzoly a poté uvolní doménu aplikace.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Programování s aplikačními doménami](application-domains.md#programming-with-application-domains)
- [Používání domén aplikací](use.md)
