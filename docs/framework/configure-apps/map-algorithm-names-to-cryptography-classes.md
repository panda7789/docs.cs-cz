---
title: Mapování názvů algoritmů na třídy šifrování
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 87b428fffac98b4490a67e4713b56ec6e8fdcfe9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569190"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Mapování názvů algoritmů na třídy šifrování
Existují čtyři způsoby Vývojář můžete vytvořit pomocí objektu kryptografie [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   Vytvoření objektu pomocí **nové** operátor.  
  
-   Vytvoření objektu, který implementuje konkrétní kryptografický algoritmus voláním **vytvořit** metodu na abstraktní třídu pro tento algoritmus.  
  
-   Vytvoření objektu, který implementuje konkrétní kryptografický algoritmus voláním <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody.  
  
-   Vytvoření objektu, který implementuje třídu kryptografické algoritmy (například symetrický blokových šifrách) voláním **vytvořit** metodu na abstraktní třídu pro daný typ algoritmus (například <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 Předpokládejme například, že si vývojář chce vypočítá hodnotu hash SHA1 sadu bajtů. <xref:System.Security.Cryptography> Obor názvů obsahuje dvě implementace algoritmus SHA1, jedna implementace čistě spravovaná a ten, který zabaluje rozhraní CryptoAPI. Vývojář můžete zvolit pro vytvoření instance na konkrétní implementace SHA1 (například <xref:System.Security.Cryptography.SHA1Managed>) voláním **nové** operátor. Pokud však není důležité, která třída načte modul common language runtime, za předpokladu, třída implementuje algoritmus hash SHA1, Vývojář můžete vytvořit objekt voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> metody. Tato metoda volá **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, které musí vracet implementace algoritmu hash SHA1.  
  
 Můžete také volat Vývojář **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** proto, že ve výchozím nastavení, konfigurace kryptografie zahrnuje krátké názvy algoritmů dodáváno v rozhraní .NET Framework.  
  
 Pokud není důležité, které hashovací algoritmus se používá, můžete volat Vývojář <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> metodu, která vrací objekt, který implementuje hash transformace.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Mapování názvů algoritmů v konfiguračních souborech  
 Ve výchozím nastavení, vrátí modul runtime <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objekt pro všechny čtyři scénáře. Správce počítače však můžete změnit typ objektu, který vrátí metody v posledních dvou případech. K tomu je nutné mapovat algoritmus popisný název pro třídu, kterou chcete použít v konfiguračním souboru počítače (Machine.config).  
  
 Následující příklad ukazuje postup při konfiguraci modulu runtime, aby **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, a  **System.Security.Cryptography.HashAlgorithm.Create** vrátit `MySHA1HashClass` objektu.  
  
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
  
 Můžete zadat název atributu v [< cryptoclass –\> element](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (z předchozího příkladu názvy atributu `MySHA1Hash`). Hodnota atributu v  **\<cryptoclass – >** element je řetězec, který modul common language runtime používá k nalezení třídy. Můžete použít libovolný řetězec, který splňuje požadavky uvedené v [zadání plně kvalifikované názvy typů](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Mnoho názvů algoritmů můžete namapovat na stejnou třídu. [ \<NameEntry > element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) třídy se mapuje na jeden algoritmus popisný název. **Název** atribut může být buď řetězec, který se používá při volání **System.Security.Cryptography.CryptoConfig.CreateFromName** metody nebo název třídy abstraktní šifrování v <xref:System.Security.Cryptography> oboru názvů. Hodnota **třídy** atributu se názvu atributu v  **\<cryptoclass – >** elementu.  
  
> [!NOTE]
>  Algoritmus SHA1 můžete získat voláním <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> nebo **Security.CryptoConfig.CreateFromName("SHA1")** metody. Jednotlivé metody pouze zaručuje, že vrátí objekt, který implementuje algoritmus SHA1. Není nutné mapovat každý popisný název algoritmu pro tutéž třídu v konfiguračním souboru.  
  
 Seznam výchozích názvů a třídy jsou mapovány najdete v tématu <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Viz také:
- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
- [Konfigurace šifrovacích tříd](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
