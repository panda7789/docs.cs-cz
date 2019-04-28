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
ms.openlocfilehash: ba11eed316e227ceae4cb5acecb2b081fa8868f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705529"
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
