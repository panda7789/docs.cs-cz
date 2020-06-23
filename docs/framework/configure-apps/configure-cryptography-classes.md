---
title: Konfigurace šifrovacích tříd
description: Pochopte, jak můžou správci počítačů nakonfigurovat výchozí kryptografické algoritmy a implementace algoritmů, které využívají rozhraní .NET a aplikace.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 5d12aae31ec78f80bea7df1bb0f37ac78dc37de2
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105067"
---
# <a name="configuring-cryptography-classes"></a>Konfigurace šifrovacích tříd
Windows SDK umožňuje správcům počítačů nakonfigurovat výchozí kryptografické algoritmy a implementace algoritmů, které používají .NET Framework a správné psané aplikace.  Například podnik, který má vlastní implementaci kryptografického algoritmu, může tuto implementaci nastavit jako výchozí místo implementace dodávané v Windows SDK. I když spravované aplikace, které používají kryptografii, se můžou vždy výslovně navazovat na konkrétní implementaci, doporučujeme, aby vytvářeli kryptografické objekty pomocí konfiguračního systému šifrování.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování názvů algoritmů na třídy šifrování](map-algorithm-names-to-cryptography-classes.md)  
 Popisuje, jak namapovat název algoritmu na kryptografickou třídu.  
  
 [Mapování identifikátorů objektů na algoritmy šifrování](map-object-identifiers-to-cryptography-algorithms.md)  
 Popisuje, jak namapovat identifikátor objektu na kryptografický algoritmus.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kryptografické služby](../../standard/security/cryptographic-services.md)  
 Poskytuje přehled kryptografických služeb poskytovaných Windows SDK.  
  
 [Schéma nastavení šifrování](./file-schema/cryptography/index.md)  
 Popisuje prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.
