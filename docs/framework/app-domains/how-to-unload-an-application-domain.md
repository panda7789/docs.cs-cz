---
title: 'Postupy: Uvolnění domény aplikace'
description: Přečtěte si, jak uvolnit doménu aplikace v rozhraní .NET pomocí metody AppDomain. Unload k bezproblémovému vypnutí zadané domény aplikace.
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
ms.openlocfilehash: b64a9553f63aa4a8deb57f23a97fa464edd64fee
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104682"
---
# <a name="how-to-unload-an-application-domain"></a>Postupy: Uvolnění domény aplikace
Po dokončení používání domény aplikace ji uvolněte pomocí <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody. Metoda **Unload** řádně vypne zadanou doménu aplikace. Během procesu uvolňování nemohou žádná nová vlákna přistupovat k doméně aplikace a jsou uvolněny všechny datové struktury specifické pro doménu aplikace.  
  
 Sestavení načítaná do domény aplikace jsou odebrána a již nejsou k dispozici. Pokud je sestavení v doméně aplikace neutrální vzhledem k doméně, data pro sestavení zůstanou v paměti, dokud se celý proces nevypne. Neexistuje žádný mechanismus pro uvolnění mezidoménově neutrálních sestavení než vypnutí celého procesu. Existují situace, kdy požadavek na uvolnění domény aplikace nefunguje a má za následek <xref:System.CannotUnloadAppDomainException> .  
  
 Následující příklad vytvoří novou doménu aplikace s názvem `MyDomain` , vytiskne některé informace do konzoly a poté uvolní doménu aplikace. Všimněte si, že se kód pak pokusí vytisknout popisný název uvolněné domény aplikace do konzoly. Tato akce generuje výjimku, která je zpracována příkazy try/catch na konci programu.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Programování s aplikačními doménami](application-domains.md#programming-with-application-domains)
- [Postupy: Vytvoření domény aplikace](how-to-create-an-application-domain.md)
- [Používání domén aplikací](use.md)
