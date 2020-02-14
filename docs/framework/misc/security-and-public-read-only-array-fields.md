---
title: Zabezpečené a veřejné položky pole určené pouze pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 215e8136b4bc3f2982cdb2d8382b0eca6a881f9b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217039"
---
# <a name="security-and-public-read-only-array-fields"></a>Zabezpečené a veřejné položky pole určené pouze pro čtení
Nikdy nepoužívejte pole veřejné pole jen pro čtení ze spravovaných knihoven k definování chování hranic nebo zabezpečení vašich aplikací, protože pole veřejné pole jen pro čtení lze upravovat.  
  
## <a name="remarks"></a>Poznámky  
 Některé třídy rozhraní .NET Framework obsahují veřejná pole jen pro čtení, která obsahují parametry hranice specifické pro platformu.  Například pole <xref:System.IO.Path.InvalidPathChars> je pole, které popisuje znaky, které nejsou povoleny v řetězci cesty k souboru.  Celá řada podobných polí je přítomna v celém .NET Framework.  
  
 Hodnoty veřejných polí jen pro čtení, jako <xref:System.IO.Path.InvalidPathChars> lze upravit pomocí kódu nebo kódu, který sdílí doménu aplikace vašeho kódu.  Nepoužívejte pole veřejné pole jen pro čtení, jako je například, k definování chování hranic vašich aplikací.  Pokud tak učiníte, škodlivý kód může změnit definice hranic a použít váš kód neočekávaným způsobem.  
  
 Ve verzi 2,0 a novějším .NET Framework byste měli použít metody, které vracejí nové pole namísto použití polí veřejné pole.  Například namísto použití pole <xref:System.IO.Path.InvalidPathChars> byste měli použít metodu <xref:System.IO.Path.GetInvalidPathChars%2A>.  
  
 Všimněte si, že typy .NET Framework nepoužívají veřejné pole k definování typů hranic interně.  Místo toho .NET Framework používá oddělená soukromá pole.  Změna hodnot těchto veřejných polí nezmění chování .NET Frameworkch typů.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
