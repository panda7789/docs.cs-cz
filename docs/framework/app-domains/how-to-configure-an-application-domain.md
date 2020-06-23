---
title: 'Postupy: Konfigurace domény aplikace'
description: Nakonfigurujte doménu aplikace v rozhraní .NET. Modul CLR lze poskytnout pomocí informací o konfiguraci pro novou doménu aplikace pomocí třídy AppDomainSetup.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
ms.openlocfilehash: 27afcf161bec74143fafb5dceb20597de73e23d4
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104860"
---
# <a name="how-to-configure-an-application-domain"></a>Postupy: Konfigurace domény aplikace
Modul CLR (Common Language Runtime) můžete zadat s informacemi o konfiguraci pro novou doménu aplikace pomocí <xref:System.AppDomainSetup> třídy. Při vytváření vlastních aplikačních domén je nejdůležitější vlastností <xref:System.AppDomainSetup.ApplicationBase%2A> . Další vlastnosti **AppDomainSetup** jsou používány převážně hostiteli modulu runtime ke konfiguraci konkrétní domény aplikace.  
  
 Vlastnost **ApplicationBase** definuje kořenový adresář aplikace. Pokud modul runtime potřebuje, aby splňoval požadavek typu, vyhledá sestavení obsahující typ v adresáři určeném vlastností **ApplicationBase** .  
  
> [!NOTE]
> Nová aplikační doména dědí pouze vlastnost **ApplicationBase** tvůrce.  
  
 Následující příklad vytvoří instanci třídy **AppDomainSetup** , používá tuto třídu k vytvoření nové domény aplikace, zapisuje informace do konzoly a poté uvolní doménu aplikace.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Programování s aplikačními doménami](application-domains.md#programming-with-application-domains)
- [Používání domén aplikací](use.md)
