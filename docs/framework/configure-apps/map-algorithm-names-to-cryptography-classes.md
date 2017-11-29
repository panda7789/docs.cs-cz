---
title: "Mapování názvů algoritmů na třídy šifrování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e59b2551545b8b70bcb54a5d43d041c44579b786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Mapování názvů algoritmů na třídy šifrování
Existují čtyři způsoby Vývojář můžete vytvořit objekt šifrování pomocí [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   Vytvoření objektu služby pomocí **nové** operátor.  
  
-   Vytvoření objektu, který implementuje algoritmus šifrování konkrétní voláním **vytvořit** metodu pro abstraktní třídu pro tento algoritmus.  
  
-   Vytvoření objektu, který implementuje algoritmus šifrování konkrétní voláním <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metoda.  
  
-   Vytvoření objektu, který implementuje třídu kryptografické algoritmy (například symetrický bloku šifru) voláním **vytvořit** metodu pro abstraktní třídu pro tento typ algoritmu (například <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 Předpokládejme například, že vývojář chce výpočetní algoritmus hash SHA1 sada bajtů. <xref:System.Security.Cryptography> Obor názvů obsahuje dvě implementace algoritmus SHA1, jeden čistě spravované implementace a ten, který zabalí rozhraní CryptoAPI. Vývojář můžete vytvořit instanci konkrétní implementace SHA1 (například <xref:System.Security.Cryptography.SHA1Managed>) voláním **nové** operátor. Pokud však není důležité, které třídy modulu CLR načte tak dlouho, dokud třída implementuje algoritmus hash SHA1, vývojář může vytvořit objekt voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metoda. Tato metoda volá **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, které musí vracet implementace algoritmu hash SHA1.  
  
 Vývojář může také zavolat **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** proto, že ve výchozím nastavení, konfiguraci šifrování zahrnuje krátké názvy pro algoritmy dodaný v rozhraní .NET Framework.  
  
 Pokud není důležité, který algoritmus hash se používá, můžete volat Vývojář <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metoda, která vrátí objekt, který implementuje hash transformace.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Mapování názvů algoritmů v konfiguračních souborech  
 Ve výchozím nastavení, vrátí modul runtime <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objekt pro všechny čtyři scénáře. Počítač správce ale můžete změnit typ objektu, který vrátí metody v posledních dvou scénářů. Chcete-li to provést, je nutné mapovat do třídy, na kterou chcete použít v konfiguračním souboru počítače (Machine.config) algoritmus popisný název.  
  
 Následující příklad ukazuje, jak nakonfigurovat modul runtime, aby **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, a  **System.Security.Cryptography.HashAlgorithm.Create** vrátit `MySHA1HashClass` objektu.  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 Můžete zadat název atributu v [< cryptoclass –\> element](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (předchozí příklad názvy atribut `MySHA1Hash`). Hodnota atributu v  **\<cryptoclass – >** element je řetězec, který modul common language runtime používá k nalezení třídy. Můžete použít libovolný řetězec, který splňuje požadavky uvedené v [určení plně kvalifikované názvy typů](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Mnoho názvů algoritmů namapovat na stejnou třídu. [ \<NameEntry > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mapuje třídu jeden algoritmus popisný název. **Název** atribut může být buď řetězec, který se používá při volání metody **System.Security.Cryptography.CryptoConfig.CreateFromName** metoda nebo název třídy abstraktní kryptografie v <xref:System.Security.Cryptography> oboru názvů. Hodnota **třída** atribut je název atributu v  **\<cryptoclass – >** element.  
  
> [!NOTE]
>  Můžete získat algoritmus SHA1 voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> nebo **Security.CryptoConfig.CreateFromName("SHA1")** metoda. Každá metoda pouze zaručuje, že vrátí objekt, který implementuje algoritmus SHA1. Nemáte k mapování jednotlivých popisný název algoritmu na stejnou třídu v konfiguračním souboru.  
  
 Seznam výchozích názvů a třídy jsou mapovány najdete v tématu <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Viz také  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)  
 [Konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
