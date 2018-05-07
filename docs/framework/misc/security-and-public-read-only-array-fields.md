---
title: Zabezpečené a veřejné položky pole určené pouze pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0110bb42775d8a5df9ca268b35db3abaffec84f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-public-read-only-array-fields"></a>Zabezpečené a veřejné položky pole určené pouze pro čtení
Nikdy nepoužívejte jen pro čtení veřejné položky pole ze spravovaných knihoven k definování chování hranice nebo zabezpečení aplikací, protože lze upravit jen pro čtení veřejné položky pole.  
  
## <a name="remarks"></a>Poznámky  
 Některé třídy rozhraní .NET framework obsahovat jen pro čtení veřejná pole obsahující parametry specifické pro platformu hranic.  Například <xref:System.IO.Path.InvalidPathChars> je pole, která popisuje znaky, které nejsou povoleny v řetězci cesty k souboru.  Mnoho podobné polí jsou k dispozici v rámci rozhraní .NET Framework.  
  
 Hodnoty veřejná pole jen pro čtení, například <xref:System.IO.Path.InvalidPathChars> mohou být upravena kód nebo kód, který sdílí doménu aplikace vašeho kódu.  Jen pro čtení veřejné položky pole takto byste neměli používat k definování hranice chování vaší aplikace.  Pokud tak učiníte, škodlivý kód můžete změnit definice hranic a použít kód neočekávaným způsobem.  
  
 Ve verzi 2.0 a později rozhraní .NET Framework měli byste použít metody, které vrací nové pole místo použití veřejné položky pole.  Například místo použití <xref:System.IO.Path.InvalidPathChars> pole, měli byste použít <xref:System.IO.Path.GetInvalidPathChars%2A> metoda.  
  
 Všimněte si, že typy rozhraní .NET Framework nepoužívejte veřejná pole k definování typů hranic interně.  Místo toho rozhraní .NET Framework používá oddělené soukromé položky.  Změna hodnoty těchto polí veřejné nezmění chování typů rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
