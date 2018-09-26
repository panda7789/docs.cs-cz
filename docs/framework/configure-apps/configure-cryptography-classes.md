---
title: Konfigurace šifrovacích tříd
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b9153b4525063d6c52e22d754d68ffa42e914d00
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074898"
---
# <a name="configuring-cryptography-classes"></a>Konfigurace šifrovacích tříd
[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Umožňuje správcům počítači nakonfigurovat výchozí kryptografické algoritmy a algoritmus implementace, které rozhraní .NET Framework a odpovídajícím způsobem vytvořené aplikace použít.  Například organizace, která má vlastní implementaci kryptografický algoritmus mohli tuto implementaci výchozí namísto provádění, poskytuje [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]. I když spravovaných aplikací, které používají šifrování lze vybrat vždy explicitně vytvořit vazbu na konkrétní implementaci, se doporučuje, že kryptografické objekty vytvořit pomocí konfigurace kryptografie systému.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování názvů algoritmů na třídy šifrování](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Popisuje, jak namapovat název algoritmu na kryptografickou třídu.  
  
 [Mapování identifikátorů objektů na algoritmy šifrování](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 Popisuje, jak namapovat identifikátor objektu na kryptografický algoritmus.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)  
 Obsahuje základní informace o kryptografických služeb [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].  
  
 [Schéma nastavení šifrování](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 Popisuje elementy, které mapují popisné názvy algoritmů tříd, které implementují algoritmy šifrování.
