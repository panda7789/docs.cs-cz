---
title: 'Postupy: Registrace a konfigurace monikeru služby'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: dfac833cc7517af00d0264fc5d11fc83ae543569
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313577"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Postupy: Registrace a konfigurace monikeru služby
Před použitím monikeru služby Windows Communication Foundation (WCF) v rámci aplikace modelu COM s typem kontraktu, musí zaregistrovat požadované typy s atributy s modelem COM a konfigurace aplikace modelu COM a zástupný název požadované vazby konfigurace.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Zaregistrovat s atributy požadované typy modelu COM  
  
1. Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj k načtení metadat kontraktu služby WCF. Tím se vytvoří zdrojový kód pro sestavení klienta WCF a konfigurační soubor aplikace klienta.  
  
2. Ujistěte se, že typy v sestavení jsou označeny jako `ComVisible`. Uděláte to tak, přidejte následující atribut souboru AssemblyInfo.cs projektu sady Visual Studio.  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3. Kompilaci spravovaného klienta WCF jako sestavení se silným názvem. Tento postup vyžaduje přihlášení pomocí páru kryptografických klíčů. Další informace najdete v tématu [podepisování sestavení silným názvem](https://go.microsoft.com/fwlink/?LinkId=94874) v příručce pro vývojáře .NET.  
  
4. Nástroj Assembly Registration (Regasm.exe) se `/tlb` možnost zaregistrovat typy v sestavení s modelu COM.  
  
5. Použijte nástroj Global Assembly Cache (Gacutil.exe) Chcete-li přidat sestavení do globální mezipaměti sestavení.  
  
    > [!NOTE]
    >  Podepisování sestavení a jeho přidání do globální mezipaměti sestavení jsou volitelné kroky, ale jejich může zjednodušit proces načítání sestavení ze správné místo v době běhu.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>Konfigurace aplikace COM a zástupný název s konfigurací požadované vazby  
  
-   Umístit definic vazeb (generovaných [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) v konfiguračním souboru aplikace generovaného klienta) v konfiguračním souboru aplikace klienta. Například pro Visual Basic 6.0 spustitelný soubor s názvem CallCenterClient.exe, by měl umístit konfiguraci do souboru s názvem CallCenterConfig.exe.config v rámci stejného adresáře jako spustitelný soubor. Klientská aplikace teď můžete použít zástupný název. Všimněte si, že konfigurace vazby není povinný, pokud pomocí jedné z standardních vazby typy poskytované službou WCF.  
  
     Následující typ je registrován.  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     Aplikace je přístupné přes `wsHttpBinding` vazby. Pro daný typ a konfigurace aplikace se používají následující řetězce monikeru příklad.  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Můžete použít kteroukoli z těchto řetězců moniker z aplikace Visual Basic 6.0, po přidání odkazu na sestavení, které obsahuje `IMathService` typů, jak je znázorněno v následujícím ukázkovém kódu.  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     V tomto příkladu definici pro konfiguraci vazby `Binding1` je uložen v vhodně pojmenované konfigurační soubor pro klientskou aplikaci, jako je například vb6appname.exe.config.  
  
    > [!NOTE]
    >  Podobný kód v C#, C++ nebo jakékoli jiné aplikace jazyk .NET můžete použít.  
  
    > [!NOTE]
    >  : Pokud je moniker je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chybu "Neplatná syntaxe". Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.  
  
     I když toto téma se zaměřuje na použití monikeru služby z kódu jazyka Visual Basic 6.0, je použití monikeru služby z jiných jazyků. Při použití monikeru z C++ kódu Svcutil.exe generovaného sestavení by měly být naimportovány s "no_namespace named_guids – raw_interfaces_only", jak je znázorněno v následujícím kódu.  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     To definice importované rozhraní upraví tak, aby všechny metody vrátit `HResult`. Všechny ostatní vrácené hodnoty se převedou na výstupní parametry. Celkové provádění metody zůstává stejná. To umožňuje určit, proč výjimku při volání metody na proxy serveru. Tato funkce je dostupná pouze z kódu jazyka C++.  
  
## <a name="see-also"></a>Viz také:

- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
