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
ms.openlocfilehash: 77f26405792ac782f2a04e174e8165a09b7f22f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567330"
---
# <a name="configuring-cryptography-classes"></a>Konfigurace šifrovacích tříd
Windows SDK umožňuje správcům počítačů nakonfigurovat výchozí kryptografické algoritmy a implementace algoritmů, které používají .NET Framework a správné psané aplikace.  Například podnik, který má vlastní implementaci kryptografického algoritmu, může tuto implementaci nastavit jako výchozí místo implementace dodávané v Windows SDK. I když spravované aplikace, které používají kryptografii, se můžou vždy výslovně navazovat na konkrétní implementaci, doporučujeme, aby vytvářeli kryptografické objekty pomocí konfiguračního systému šifrování.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování názvů algoritmů na třídy šifrování](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Popisuje, jak namapovat název algoritmu na kryptografickou třídu.  
  
 [Mapování identifikátorů objektů na algoritmy šifrování](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 Popisuje, jak namapovat identifikátor objektu na kryptografický algoritmus.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)  
 Poskytuje přehled kryptografických služeb poskytovaných Windows SDK.  
  
 [Schéma nastavení šifrování](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 Popisuje prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.
