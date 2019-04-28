---
title: 'Postupy: Uvolnění domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3011bd0327440cd04d5eccf5f88c036ddd76267
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705581"
---
# <a name="how-to-unload-an-application-domain"></a>Postupy: Uvolnění domény aplikace
Po dokončení používání domény aplikace, odinstalovat ji pomocí <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody. **Uvolnění** metoda řádně ukončí zadanou doménu aplikace. Během procesu uvolnění žádná nová vlákna můžete přístup k doméně aplikace a všechny aplikace domény specifické datové struktury jsou uvolněny.  
  
 Sestavení načtena do domény aplikace jsou odebrány a nadále již nebudou k dispozici. Pokud je sestavení v aplikační doméně doménově neutrální, zůstávají data pro sestavení v paměti, dokud nebude ukončen celý proces. Neexistuje žádný mechanismus uvolnění sestavení jako doménově neutrální než celý proces ukončen. Existují situace, kdy požadavek na uvolnění domény aplikace nefunguje, výsledkem <xref:System.CannotUnloadAppDomainException>.  
  
 Následující příklad vytvoří novou doménu aplikace volá `MyDomain`, vypíše některé informace o do konzoly a potom uvolnění domény aplikace. Všimněte si, že kód poté se pokusí tisk popisný název uvolněné doméně aplikace do konzoly. Tato akce vygeneruje výjimku, která zpracovává příkazy try/catch – na konci programu.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Programování pomocí domén aplikace](application-domains.md#programming-with-application-domains)
- [Postupy: Vytvoření domény aplikace](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)
- [Používání domén aplikací](../../../docs/framework/app-domains/use.md)
