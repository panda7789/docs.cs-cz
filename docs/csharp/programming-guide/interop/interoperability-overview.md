---
title: Přehled interoperability (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
ms.openlocfilehash: 0bd53d97cec4370adc78fc715b1cea5ee5a3fd6f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43860439"
---
# <a name="interoperability-overview-c-programming-guide"></a>Přehled interoperability (Průvodce programováním v C#)
Téma popisuje metody, a umožňuje interoperabilitu mezi kód jazyka C# spravovaného a nespravovaného kódu.  
  
## <a name="platform-invoke"></a>Vyvolání platformy  
 *Vyvolání platformy* je služba, umožňuje spravovaným kódu volat nespravované funkce, které jsou implementovány v dynamické knihovny (DLL), jako například sítě na rozhraní Microsoft Win32 API. Vyhledá a volá exportované funkce a zařadí argumenty (celá čísla, řetězce, pole, struktury a tak dále) napříč hranicemi podle potřeby.  
  
 Další informace najdete v tématu [používání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) a [postupy: použití vyvolání platformy pro přehrání souboru Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Common Language Runtime](../../../standard/clr.md) (CLR) spravuje přístup k systémovým prostředkům. Volání nespravovaného kódu, který je mimo rámec platformy CLR obchází tento mechanismus zabezpečení a proto představuje bezpečnostní riziko. Nespravovaný kód například může volat prostředky v nespravovaném kódu přímo, bez použití mechanismy zabezpečení CLR. Další informace najdete v tématu [zabezpečení v rozhraní .NET](../../../standard/security/index.md).  
  
## <a name="c-interop"></a>interoperabilita C++  
 Interoperabilita C++, označované také jako ho právě funguje (IJW), můžete použít k zabalení nativních tříd jazyka C++, takže mohou být spotřebovány kód, který se vytváří v jazyce C# nebo jiný jazyk rozhraní .NET Framework. K tomuto účelu můžete psát kód C++ zalomení nativní knihovnu DLL nebo klasické komponenty COM. Na rozdíl od jiných jazycích rozhraní .NET Framework [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] má interoperability podporu, která umožňuje spravovaného a nespravovaného kódu budou umístěné ve stejné aplikaci a dokonce i ve stejném souboru. Potom sestavíte kódu jazyka C++ s použitím **/CLR** přepínače kompilátoru pro vytvoření spravované sestavení. Nakonec přidejte odkaz na sestavení v projektu C# a použít zabalenou objektů, stejně jako ostatní spravované třídy.  
  
## <a name="exposing-com-components-to-c"></a>Vystavení komponent COM pro C#  
 Můžete využívat komponenty modelu COM z projektu v jazyce C#. Obecné kroky jsou následující:  
  
1.  Vyhledejte komponentu modelu COM použít a její registrace. Použijte regsvr32.exe k registraci nebo zrušení – registrace modelu COM DLL.  
  
2.  Přidejte do projektu odkaz na komponentu nebo typ knihovny modelu COM.  
  
     Když přidáte odkaz, použije sada Visual Studio [Tlbimp.exe (Importér knihovny typů)](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), který by knihovnu typů jako vstup do výstupního sestavení vzájemné spolupráce rozhraní .NET Framework. Sestavení, také s názvem obálka volatelná aplikacemi běhu (RCW), obsahuje spravované třídy a rozhraní, které balí třídy modelu COM a rozhraní, která jsou v knihovně typů. Visual Studio přidá do projektu odkaz na vygenerované sestavení.  
  
3.  Vytvoření instance třídy, která je definována v RCW. To, pak vytvoří instanci objektu COM.  
  
4.  Pomocí objektu stejným způsobem, jako jiné spravované objekty. Pokud objekt je uvolněn systémem uvolňování paměti, instance objektu COM je také uvolněn z paměti.  
  
 Další informace najdete v tématu [vystavení komponent COM pro rozhraní .NET Framework](../../../../docs/framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Vystavení C# do modelu COM  
 C# typy, které byly správně vystavit mohou používat klienti modelu COM. Základní kroky ke zveřejnění typů jazyka C# jsou následující:  
  
1.  Přidáte atributů spolupráce v projektu C#.  
  
     Sestavení modelu COM lze zviditelnit úpravou vlastností projektu Visual C#. Další informace najdete v tématu [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Generovat knihovnu typů modelu COM, zaregistrujte je pro použití modelu COM.  
  
     Visual C# vlastnosti projektu na automatickou registraci sestavení C# pro spolupráci s COM můžete upravit. Visual Studio používá [Regasm.exe (Nástroj registrace sestavení)](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md), použije `/tlb` přepínač příkazového řádku, který přebírá spravované sestavení jako vstup, chcete-li generovat knihovnu typů. Popisuje tuto knihovnu typů `public` typy v sestavení a přidá položky registru tak, aby klienti modelu COM, můžete vytvořit spravované třídy.  
  
 Další informace najdete v tématu [vystavení komponent architektury .NET Framework pro COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md) a [Ukázka třídy COM](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Viz také

- [Zlepšení výkonu interoperability](https://msdn.microsoft.com/library/ms998551.aspx)  
- [Úvod do vzájemná funkční spolupráce mezi modelem COM a .NET](https://msdn.microsoft.com/library/office/bb610378.aspx)  
- [Představení zprostředkovatele komunikace s objekty COM v jazyce Visual Basic](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
- [Zařazování mezi spravovaným a nespravovaným kódem](../../../../docs/framework/interop/interop-marshaling.md)  
- [Spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
