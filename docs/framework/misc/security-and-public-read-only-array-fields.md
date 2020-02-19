---
title: Zabezpečené a veřejné položky pole určené pouze pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 2df4acc0606e4fe8fccee4a8acc6ab744dcbbb71
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452705"
---
# <a name="security-and-public-read-only-array-fields"></a>Zabezpečené a veřejné položky pole určené pouze pro čtení
Nikdy nepoužívejte pole veřejné pole jen pro čtení ze spravovaných knihoven k definování chování hranic nebo zabezpečení vašich aplikací, protože pole veřejné pole jen pro čtení lze upravovat.  
  
## <a name="remarks"></a>Poznámky  

Některé třídy .NET obsahují veřejná pole jen pro čtení, která obsahují parametry hranice specifické pro platformu. Například pole <xref:System.IO.Path.InvalidPathChars> je pole, které popisuje znaky, které nejsou povoleny v řetězci cesty k souboru. Celá řada podobných polí je k dispozici v rámci .NET.  
  
 Hodnoty veřejných polí jen pro čtení, jako <xref:System.IO.Path.InvalidPathChars> lze upravit pomocí kódu nebo kódu, který sdílí doménu aplikace vašeho kódu.  Nepoužívejte pole veřejné pole jen pro čtení, jako je například, k definování chování hranic vašich aplikací.  Pokud tak učiníte, škodlivý kód může změnit definice hranic a použít váš kód neočekávaným způsobem.  
  
 Ve verzi 2,0 a novějším .NET Framework byste měli použít metody, které vracejí nové pole namísto použití polí veřejné pole.  Například namísto použití pole <xref:System.IO.Path.InvalidPathChars> byste měli použít metodu <xref:System.IO.Path.GetInvalidPathChars%2A>.  
  
 Všimněte si, že typy .NET Framework nepoužívají veřejné pole k definování typů hranic interně.  Místo toho .NET Framework používá oddělená soukromá pole.  Změna hodnot těchto veřejných polí nezmění chování .NET Frameworkch typů.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
