---
title: Zajištění integrity dat pomocí hodnot hash
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268744"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Zajištění integrity dat pomocí hodnot hash
Hodnota hash je číselná hodnota pevnou délku, která jednoznačně identifikuje data. Hodnoty hash znázornění velkých objemů dat jako mnohem menší číselných hodnot, tak se používají v digitální podpisy. Hodnota hash se můžete přihlásit efektivnější než podepisování větší hodnotu. Hodnoty hash jsou také užitečná pro ověření integrity dat posílaných prostřednictvím nezabezpečených kanálů. Hodnota hash přijatá data je možné porovnat s hodnoty hash dat, protože byla odeslána k určení, zda byla data změněna.  
  
 Toto téma popisuje, jak vytvořit a ověřit hash kódy s využitím tříd v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.  
  
## <a name="generating-a-hash"></a>Generování hodnoty Hash  
 Třídy spravované hash může hash pole bajtů nebo objekt spravovaný datový proud. Následující příklad používá algoritmus hash SHA1 vytvořit hodnotu hash pro řetězce. V příkladu se používá <xref:System.Text.UnicodeEncoding> pro převod řetězce na pole bajtů, které jsou hashována pomocí <xref:System.Security.Cryptography.SHA1Managed> třídy. Hodnota hash se pak zobrazí v konzole.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Tento kód se zobrazí následující řetězec do konzoly:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Ověření hodnoty Hash  
 Data je možné porovnat s hodnotou hash k určení jeho integritu. Obvykle data se po zahašování použije v určitém čase a hodnota hash je chráněn nějakým způsobem. Data můžete kdykoli později, znovu vytvořit otisk a ve srovnání s chráněná hodnota. Pokud se hodnoty hash shodují, data nikdo nezměnil. Pokud hodnoty nejsou shodné, data byla poškozena. Pro tento systém fungovat musí být šifrované nebo udržen v tajnosti před všechny nedůvěryhodní chráněné hash.  
  
 Následující příklad porovnává předchozí hodnotu hash řetězce na novou hodnotu hash. V tomto příkladu prochází každý bajt hodnoty hash a provádí porovnání.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Pokud tyto hodnoty hash shodují, zobrazí tento kód do konzoly následující:  
  
```  
The hash codes match.  
```  
  
 Pokud shodné nejsou, zobrazí následující kód:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Viz také:

- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
