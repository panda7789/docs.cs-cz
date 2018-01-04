---
title: "Zajištění integrity dat pomocí hodnot hash"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fcede920b0e57dee0449d8ff6d7c935b177dcbcd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Zajištění integrity dat pomocí hodnot hash
Hodnota hash je číselná hodnota pevnou délku, která jednoznačně identifikuje data. Hodnoty hash představují velké objemy dat jako mnohem menší číselné hodnoty, takže se používají s digitálními podpisy. Hodnota hash je možné podepsat efektivnější než velkou hodnotu. Hodnoty hash jsou taky užitečné pro ověření integrity dat odeslaných v nezabezpečené kanály. Hodnota hash přijatých dat. lze porovnat hodnotu hash dat, jako byl odeslán k určení, zda byla změněna data.  
  
 Toto téma popisuje, jak vytvořit a ověřit kódů hash pomocí třídy v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.  
  
## <a name="generating-a-hash"></a>Generování hodnoty Hash  
 Spravované hash třídy můžete hash pole bajtů nebo objekt spravovaného streamu. Následující příklad používá algoritmus hash SHA1 vytvořit hodnotu hash pro řetězec. V příkladu se používá <xref:System.Text.UnicodeEncoding> třída převést řetězec na pole bajtů, které jsou hashována pomocí <xref:System.Security.Cryptography.SHA1Managed> třídy. Hodnota hash se následně zobrazí ke konzole.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Tento kód se zobrazí následující řetězec do konzoly:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Ověření hodnoty Hash  
 Data lze porovnat s hodnotou hash určit jeho integritu. Obvykle se rozdělí data v určitém čase a hodnota hash je chráněný nějakým způsobem. Data můžete později, znovu rozdělí a porovnání s chráněná hodnota. Pokud se hodnoty hash shodují, data nikdo nezměnil. Pokud se hodnoty neshodují, je poškozená data. Pro tento systém fungovat musí být chráněný hash šifrované nebo náskoku před všechny nedůvěryhodní.  
  
 Následující příklad porovnává předchozí hodnotu hash řetězce na novou hodnotu hash. V tomto příkladu prochází každým bajtem hodnoty hash a provádí porovnání.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Pokud tyto hodnoty hash shodují, tento kód zobrazí následující do konzoly:  
  
```  
The hash codes match.  
```  
  
 Pokud se neshodují, zobrazí se následující kód:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Viz také  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
