---
title: Zabezpečené a veřejné položky pole určené pouze pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19b5ad73150697c1442056642a1b11d504ecc426
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113773"
---
# <a name="security-and-public-read-only-array-fields"></a>Zabezpečené a veřejné položky pole určené pouze pro čtení
Nikdy nepoužívejte pole jen pro čtení veřejné pole ze spravované knihovny k definování hranice chování nebo zabezpečení vašich aplikací, protože veřejné pole jen pro čtení pole je možné upravit.  
  
## <a name="remarks"></a>Poznámky  
 Některé třídy rozhraní .NET framework zahrnují jen pro čtení veřejné pole, které obsahují parametry specifické pro platformu hranice.  Například <xref:System.IO.Path.InvalidPathChars> pole je pole, která popisuje znaky, které nejsou povoleny v řetězci cesty k souboru.  Mnoho podobná pole jsou k dispozici v celém rozhraní .NET Framework.  
  
 Hodnoty veřejného polí jen pro čtení, jako jsou <xref:System.IO.Path.InvalidPathChars> můžete změnit váš kód nebo kód, který sdílí váš kód domény aplikace.  Veřejné pole jen pro čtení pole tímto způsobem byste neměli používat k definování hranice chování vašich aplikací.  Pokud tak učiníte, škodlivý kód může změnit definice hranic a používat váš kód neočekávaným způsobem.  
  
 Ve verzi 2.0 a novější rozhraní .NET Framework měli byste použít metody, které vracejí nové pole namísto veřejná pole.  Například místo použití <xref:System.IO.Path.InvalidPathChars> pole, měli byste použít <xref:System.IO.Path.GetInvalidPathChars%2A> metody.  
  
 Všimněte si, že typy rozhraní .NET Framework nepoužívejte veřejná pole k definování typů hranic interně.  Místo toho rozhraní .NET Framework používá samostatné privátní pole.  Změna hodnot tyto veřejné polí nezmění chování typy rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
