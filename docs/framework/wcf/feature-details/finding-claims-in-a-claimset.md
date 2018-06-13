---
title: Hledání deklarací v sadě deklarací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 7ca22d701277e71e509e6b291eb59a0223a0250c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488595"
---
# <a name="finding-claims-in-a-claimset"></a>Hledání deklarací v sadě deklarací
Zkoumání obsahu <xref:System.IdentityModel.Claims.ClaimSet> pro konkrétní typy deklarací identity je běžné úlohy při použití ověřování na základě deklarace. K prozkoumání <xref:System.IdentityModel.Claims.ClaimSet> přítomnost konkrétních deklarací identit, použijte <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metoda. Tato metoda poskytuje lepší výkon než iterování přímo přes <xref:System.IdentityModel.Claims.ClaimSet>. Následující příklad ukazuje toto použití. Všimněte si, že `claimType` a `claimRight` může být parametry `null`. V takovém případě bude parametry odpovídají všechny typy deklarací identity a deklarací identity práva.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
