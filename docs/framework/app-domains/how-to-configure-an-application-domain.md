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
ms.openlocfilehash: 012f0220afa0e444d68af5998fb2492a03a371d8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183162"
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
  
## <a name="see-also"></a>Viz také  
- [Programování pomocí domén aplikace](application-domains.md#programming-with-application-domains)  
- [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
