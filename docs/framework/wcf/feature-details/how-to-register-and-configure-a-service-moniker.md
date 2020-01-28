---
title: 'Postupy: registrace a konfigurace monikeru služby'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: fc0b2d00bcc8e3b14c491446f16297c1036b783b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747087"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Postupy: registrace a konfigurace monikeru služby

Předtím, než použijete moniker služby Windows Communication Foundation (WCF) v rámci aplikace modelu COM se zadaným kontraktem, je nutné zaregistrovat požadované typy s atributem COM a nakonfigurovat aplikaci COM a moniker s požadovanou vazbou. rozšířeného.

## <a name="register-the-required-attributed-types-with-com"></a>Registrace požadovaných typů s atributy pomocí modelu COM

1. Pomocí nástroje [Svcutil. exe (ServiceModel Metadata Utility)](../servicemodel-metadata-utility-tool-svcutil-exe.md) načtěte kontrakt metadat ze služby WCF. Tím se vygeneruje zdrojový kód pro sestavení klienta WCF a konfigurační soubor klientské aplikace.

2. Zajistěte, aby byly typy v sestavení označeny jako `ComVisible`. Chcete-li to provést, přidejte následující atribut do souboru *AssemblyInfo.cs* v projektu sady Visual Studio.

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. Zkompilujte spravovaný klient služby WCF jako sestavení se silným názvem. To vyžaduje podepisování pomocí páru kryptografických klíčů. Další informace naleznete v tématu [podepisování sestavení silným názvem](../../../standard/assembly/sign-strong-name.md).

4. Použijte nástroj registrace sestavení (Regasm. exe) s možností `-tlb` k registraci typů v sestavení pomocí modelu COM.

5. K přidání sestavení do globální mezipaměti sestavení (GAC) použijte nástroj Global Assembly Cache (Gacutil. exe).

    > [!NOTE]
    > Podpis sestavení a jeho přidání do globální mezipaměti sestavení (GAC) je volitelný postup, ale může zjednodušit proces načítání sestavení ze správného umístění za běhu.

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>Konfigurace aplikace COM a monikeru s požadovanou konfigurací vazby

- Vložte definice vazeb (generované [nástrojem Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) do generovaného konfiguračního souboru klientské aplikace) v konfiguračním souboru klientské aplikace. Například pro spustitelný soubor Visual Basic 6,0 s názvem CallCenterClient. exe by měla být konfigurace umístěna do souboru s názvem CallCenterConfig. exe. config v rámci stejného adresáře jako spustitelný soubor. Klientská aplikace může nyní použít moniker. Všimněte si, že konfigurace vazby není vyžadována, pokud používáte jeden ze standardních typů vazby poskytovaných službou WCF.

     Následující typ je zaregistrován.

    ```csharp
    using System.ServiceModel;

    [ServiceContract]
    public interface IMathService
    {
        [OperationContract]
        public int Add(int x, int y);
        [OperationContract]
        public int Subtract(int x, int y);
    }
    ```

     Aplikace je vystavena pomocí `wsHttpBinding` vazby. Pro daný typ a konfiguraci aplikace jsou použity následující příklady řetězců monikeru.

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     nebo

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     Můžete použít kterýkoli z těchto řetězců monikeru z aplikace Visual Basic 6,0 po přidání odkazu na sestavení, které obsahuje `IMathService` typy, jak je znázorněno v následujícím ukázkovém kódu.

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     V tomto příkladu je definice pro konfiguraci vazby `Binding1` uložená v vhodně pojmenovaném konfiguračním souboru pro klientskou aplikaci, jako je *vb6appname. exe. config*.

    > [!NOTE]
    > Můžete použít podobný kód v C#, C++nebo v jakékoli jiné aplikaci jazyka .NET.

    > [!NOTE]
    > Pokud je moniker poškozený nebo pokud není služba k dispozici, volání `GetObject` vrátí chybu neplatné syntaxe. Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.

     I když se toto téma zaměřuje na použití monikeru služby z kódu Visual Basic 6,0, můžete použít moniker služby z jiných jazyků. Při použití monikeru z C++ kódu by se sestavení vygenerované pomocí Svcutil. exe mělo importovat s "no_namespace named_guids raw_interfaces_only", jak je znázorněno v následujícím kódu.

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     Tím se upraví importované definice rozhraní, aby všechny metody vracely `HResult`. Jakékoli jiné návratové hodnoty jsou převedeny na výstupní parametry. Celkové provedení metod zůstává stejné. To umožňuje určit příčinu výjimky při volání metody na proxy serveru. Tato funkce je k dispozici C++ pouze z kódu.

## <a name="see-also"></a>Viz také:

- [Nástroj metadat modelu služby (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
