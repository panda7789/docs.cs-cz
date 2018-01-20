---
title: "Postupy: Konfigurace domény aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1024d41d99b9752fbbf8ef9458a8396d91c68fd0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-an-application-domain"></a>Postupy: Konfigurace domény aplikace
Modul common language runtime můžete poskytnout informace o konfiguraci pro novou doménu aplikace pomocí <xref:System.AppDomainSetup> třídy. Při vytváření vlastní domény aplikace, je nejdůležitější vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A>. Druhá **AppDomainSetup** vlastnosti jsou používány především modulu runtime pro konfiguraci určité domény aplikace.  
  
 **ApplicationBase** vlastnost definuje kořenový adresář aplikace. Když modul runtime potřebuje vyhovovaly žádosti o typ, sondy pro sestavení obsahující typ v adresáři určeného **ApplicationBase** vlastnost.  
  
> [!NOTE]
>  Nová doména aplikace dědí pouze **ApplicationBase** vlastnosti Tvůrce.  
  
 Následující příklad vytvoří instanci **AppDomainSetup** třída, používá tuto třídu k vytvoření nové domény aplikace, zapíše informace do konzoly a poté uvolní doménu aplikace.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Programování s doménami aplikací](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
