---
title: "Výraz obsahuje typ & č. 39; &lt;typename&gt;& č. 39; je v omezeném typu a nesmí být použity pro přístup členy zděděno z & č. 39; objekt & č. 39; nebo & č. 39; Typ hodnoty & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords: BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30742bd46ccd1a3e5a688ebd2621e2c8a3d50e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>Výraz obsahuje typ & č. 39; &lt;typename&gt;& č. 39; je v omezeném typu a nesmí být použity pro přístup členy zděděno z & č. 39; objekt & č. 39; nebo & č. 39; Typ hodnoty & č. 39;
Výraz vyhodnocen jako typ, který nemůže být modulem common language runtime (CLR) do pole, ale přistupuje k člena, který vyžaduje zabalení.  
  
 *Zabalení* odkazuje na zpracování potřeba převést na typ `Object` nebo v některých případech k <xref:System.ValueType>. Modul CLR nelze například pole určité typy struktura <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, a <xref:System.TypedReference>.  
  
 Tento výraz se pokusí použít typ s omezeným přístupem pro volání metody zděděno z <xref:System.Object> nebo <xref:System.ValueType>, jako například <xref:System.Object.GetHashCode%2A> nebo <xref:System.Object.ToString%2A>. Pro přístup k této metodě [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] se pokusilo konverzi implicitní zabalení, který způsobuje, že k této chybě.  
  
 **ID chyby:** BC31393  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Vyhledejte výraz, který se vyhodnocuje citovaný typu.  
  
2.  Vyhledejte část údajů, které se pokusí zavolat metodu zděděno z <xref:System.Object> nebo <xref:System.ValueType>.  
  
3.  Přepište příkaz tak, aby se zabránilo volání metody.  
  
## <a name="see-also"></a>Viz také  
 [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
