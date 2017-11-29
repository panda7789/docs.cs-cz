---
title: "Postupy: Přístup k hardwarovým šifrovacím zařízením"
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
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5156316387f94d434301e2d5286bd325d7e04320
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-access-hardware-encryption-devices"></a>Postupy: Přístup k hardwarovým šifrovacím zařízením
Můžete použít <xref:System.Security.Cryptography.CspParameters> třída pro přístup k hardwarovým šifrovacím zařízením. Tuto třídu můžete použít například k integraci vaší aplikace pomocí čipové karty, hardwaru generátoru náhodných čísel nebo hardwarové implementaci konkrétního šifrovacího algoritmu.  
  
 <xref:System.Security.Cryptography.CspParameters> Třída vytvoří zprostředkovatele kryptografických služeb (CSP), který přistupuje k šifrování zařízení správně nainstalovaný hardware.  Dostupnost zprostředkovatele kryptografických služeb můžete ověřit zkontrolováním následující klíč registru pomocí Editoru registru (Regedit.exe): HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Podepsat data pomocí klíče karty  
  
1.  Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy a předejte typ integer poskytovatele a název zprostředkovatele pro konstruktor.  
  
2.  Předat příslušné příznaky tak, aby <xref:System.Security.Cryptography.CspParameters.Flags%2A> vlastnost nově vytvořený <xref:System.Security.Cryptography.CspParameters> objektu.  Například předat <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> příznak.  
  
3.  Vytvořit novou instanci třídy <xref:System.Security.Cryptography.AsymmetricAlgorithm> – třída (například <xref:System.Security.Cryptography.RSACryptoServiceProvider> třída), předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.  
  
4.  Podepište data pomocí jedné z `Sign` metody a ověřte vaše data pomocí jedné z `Verify` metody.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Generovat náhodné číslo pomocí generátoru náhodných čísel hardwaru  
  
1.  Vytvořit novou instanci třídy <xref:System.Security.Cryptography.CspParameters> třídy a předejte typ integer poskytovatele a název zprostředkovatele pro konstruktor.  
  
2.  Vytvořit novou instanci třídy <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, předejte <xref:System.Security.Cryptography.CspParameters> objekt konstruktoru.  
  
3.  Vytvoření náhodná hodnota pomocí <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> nebo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak podepsat data pomocí čipové karty.  Příklad kódu vytvoří <xref:System.Security.Cryptography.CspParameters> objekt, který zpřístupňuje čipových karet a poté inicializuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> pomocí CSP.  Příklad kódu a podepíše a ověří některá data.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zahrnout <xref:System> a <xref:System.Security.Cryptography> obory názvů.  
  
-   Musíte mít čtečka čipových karet a ovladače, které jsou v počítači nainstalována.  
  
-   Je třeba inicializovat <xref:System.Security.Cryptography.CspParameters> pomocí informace specifické pro vaši čtečku.  Další informace najdete v dokumentaci vaši čtečku.
