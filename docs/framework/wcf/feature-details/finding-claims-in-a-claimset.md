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
ms.openlocfilehash: 1954da20d382630f965582fcc01bbaf72665720a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595450"
---
# <a name="finding-claims-in-a-claimset"></a>Hledání deklarací v sadě deklarací
Zkoumání obsahu <xref:System.IdentityModel.Claims.ClaimSet> pro konkrétní typy deklarací identity je běžný úkol při použití autorizace založené na deklaracích. <xref:System.IdentityModel.Claims.ClaimSet>Pro zjištění přítomnosti konkrétních deklarací použijte <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metodu. Tato metoda poskytuje lepší výkon než iterace přímo přes <xref:System.IdentityModel.Claims.ClaimSet> . Následující příklad demonstruje toto použití. Všimněte si, `claimType` že `claimRight` parametry a můžou být `null` . V takovém případě budou parametry odpovídat všem typům deklarací identity a nárokům na deklarace identity.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Správa deklarací a autorizace s modelem identity](managing-claims-and-authorization-with-the-identity-model.md)
