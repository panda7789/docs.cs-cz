---
title: 'Postupy: Vytváření zásad vydavatele'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e7cac3c7e6c588a82e9dfff169ba7b7aa72c35f8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028011"
---
# <a name="how-to-create-a-publisher-policy"></a>Postupy: Vytváření zásad vydavatele
Dodavatelé sestavení mohou stavu, že aplikace by měly používat novější verze sestavení zahrnutím souboru zásad vydavatele s upgradovaný sestavení. Soubor zásad vydavatele, který určuje přesměrování sestavení a nastavení základní kód a používá stejný formát jako konfigurační soubor aplikace. Soubor zásad vydavatele, který je zkompilován sestavení a umístěn v globální mezipaměti sestavení.  
  
 Při vytváření zásad vydavatele jsou tři kroky:  
  
1.  Vytvořte soubor zásad vydavatele.  
  
2.  Vytvořte sestavení zásad vydavatele.  
  
3.  Přidáte sestavení zásad vydavatele do globální mezipaměti sestavení.  
  
 Schéma pro zásady vydavatele je popsána v [přesměrování verze sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md). Následující příklad ukazuje vydavatele souboru zásad, který přesměruje jednu verzi `myAssembly` do jiného.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Zjistěte, jak určit základ kódu, naleznete v tématu [určení umístění sestavení](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Vytváření sestavení zásad vydavatele  
 Použití [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) k vytvoření sestavení zásad vydavatele.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Chcete-li vytvořit sestavení zásady vydavatele  
  
1.  Na příkazovém řádku zadejte následující příkaz:  
  
     **Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:**  *keyPairFile* **/Platform:** *processorArchitecture*  
  
     V tomto příkazu:  
  
    -   *PublisherPolicyFile* argumentem je název souboru zásad vydavatele.  
  
    -   *PublisherPolicyAssemblyFile* argumentem je název sestavení zásad vydavatele, která je výsledkem tohoto příkazu. Název souboru sestavení musí vyhovovat formátu:  
  
         **zásady.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile* argumentem je název souboru, který obsahuje pár klíčů. Musíte podepsat sestavení a sestavení zásad vydavatele s stejného páru klíčů.  
  
    -   *ProcessorArchitecture* argument určuje platformu cílem sestavení specifické pro procesor.  
  
        > [!NOTE]
        >  Možnost Cílová architektura procesoru je v rozhraní .NET Framework verze 2.0 nový.  
  
     Následující příkaz vytvoří sestavení zásad vydavatele volá `policy.1.0.myAssembly` ze souboru zásad vydavatele volá `pub.config`, přiřadí silný název sestavení pomocí páru klíčů v `sgKey.snk` souboru a určí, že sestavení, zaměřuje x86 Architektura procesoru.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     Sestavení zásad vydavatele musí odpovídat architektuře procesoru, který se vztahuje na sestavení. Proto pokud vaše sestavení <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> hodnotu <xref:System.Reflection.ProcessorArchitecture.MSIL>, sestavení zásady vydavatele pro toto sestavení je potřeba vytvořit s `/platform:anycpu`. Je nutné zadat samostatné sestavení zásady vydavatele pro každé sestavení specifické pro procesor.  
  
     V důsledku tohoto pravidla je, že chcete-li změnit na architektuře procesoru pro sestavení, je nutné změnit hlavních nebo vedlejších součást čísla verze, tak, že zadáte nové sestavení zásad vydavatele s správnou architekturu procesoru. Staré sestavení zásad vydavatele nelze služby sestavení, jakmile vaše sestavení obsahuje jinou architekturu procesoru.  
  
     Jiné důsledkem je, že má linker verze 2.0 nelze použít k vytvoření sestavení zásady vydavatele pro sestavení zkompilovaného pomocí starší verze rozhraní .NET Framework, protože vždycky určuje architekturu procesoru.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Přidání sestavení zásad vydavatele do globální mezipaměti sestavení  
 Použití [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) přidání sestavení zásad vydavatele do globální mezipaměti sestavení.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Přidání sestavení zásad vydavatele do globální mezipaměti sestavení  
  
1.  Na příkazovém řádku zadejte následující příkaz:  
  
     **Gacutil /i***publisherPolicyAssemblyFile*  
  
     Následující příkaz přidá `policy.1.0.myAssembly.dll` do globální mezipaměti sestavení.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  Sestavení zásad vydavatele nelze přidat do globální mezipaměti sestavení, pokud původní soubor zásad vydavatele se nachází ve stejném adresáři jako sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md)  
 [Konfigurace aplikací .NET Framework](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Schéma nastavení běhového prostředí](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Přesměrování verzí sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
