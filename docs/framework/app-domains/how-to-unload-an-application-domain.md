---
title: "Postupy: Uvolnění domény aplikace"
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
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58fd1477715bafa4e3455a3e476acbae3a098dbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unload-an-application-domain"></a>Postupy: Uvolnění domény aplikace
Po dokončení používání domény aplikace uvolnit pomocí <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda. **Uvolnění** metoda řádně vypne zadanou doménu aplikace. Během procesu uvolnění žádné nové vláken můžete přístup k doméně aplikace a všechny domény – konkrétní datové struktury aplikace jsou uvolněny.  
  
 Sestavení načtená do domény aplikace se odeberou a již nejsou k dispozici. Pokud je sestavení v doméně aplikace domény jazykově neutrální, zůstane data pro sestavení v paměti, dokud celý proces je vypnutý. Neexistuje žádný mechanismus k uvolnění domény jazykově neutrální sestavení než vypíná celý proces. Existují situacích, kdy požadavek na uvolnění domény aplikace nefunguje a výsledkem <xref:System.CannotUnloadAppDomainException>.  
  
 Následující příklad vytvoří novou doménu aplikace nazvanou `MyDomain`, vytiskne některé informace do konzoly a poté uvolní doménu aplikace. Všimněte si, že kód pak pokusí vytisknout popisný název domény odpojen aplikaci do konzoly. Tato akce vygeneruje výjimku, která se zpracovává souborem try/catch – příkazy na konci tohoto programu.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Programování s doménami aplikací](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Postupy: vytvoření domény aplikace](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
