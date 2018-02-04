---
title: "Přehled interoperability (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f799f86c5dc597b0fe26197ab6321b9d3e82f664
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="interoperability-overview-c-programming-guide"></a>Přehled interoperability (Průvodce programováním v C#)
Téma popisuje metody a umožňuje interoperabilitu mezi C# spravovaný kód a nespravovaného kódu.  
  
## <a name="platform-invoke"></a>Vyvolání platformy  
 *Vyvolání platformy* je služba, což umožňuje spravovat kódu volání nespravovaných funkcí, které jsou implementované v dynamické knihovny (DLL), například v rozhraní API Win32 společnosti Microsoft. Vyhledá a vyvolá exportované funkce a zařazuje její argumenty (celá čísla, řetězce, pole, struktur a tak dále) přes součinnosti hranice, podle potřeby.  
  
 Další informace najdete v tématu [využívání nespravovaných funkcí DLL](../../../framework/interop/consuming-unmanaged-dll-functions.md) a [postupy: použití vyvolání platformy pro přehrání souboru Wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).  
  
> [!NOTE]
>  [Modul Common Language Runtime](../../../standard/clr.md) (CLR) spravuje přístup k systémovým prostředkům. Volání nespravovaného kódu, který je mimo modulu CLR obchází tento mechanismus zabezpečení a proto představuje bezpečnostní riziko. Nespravovaný kód může například volání prostředky v nespravovaném kódu přímo, obcházení mechanismy zabezpečení CLR. Další informace najdete v tématu [zabezpečení rozhraní .NET Framework](https://technet.microsoft.com/en-us/security/).  
  
## <a name="c-interop"></a>interoperabilita C++  
 Interoperabilita C++, také známé jako jeho právě funguje (IJW), můžete použít k zabalení nativních tříd jazyka C++, takže mohou být spotřebovávána kód, který je vytvořené v C# nebo jiném jazyce rozhraní .NET Framework. K tomuto účelu můžete napsat kód C++ zabalit nativní knihovny DLL nebo klasické komponenty COM. Na rozdíl od jiných jazyků rozhraní .NET Framework [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] má interoperabilita podporovat, umožňuje spravovaných a nespravovaných kódu být umístěné ve stejné aplikaci a to i ve stejném souboru. Pak vytvoříte kód C++ pomocí **/CLR** přepínače kompilátoru k vytvoření spravované sestavení. Nakonec můžete přidat odkaz na sestavení v projektu C# a používat zabalené objekty stejně, jako byste použili jiné spravované třídy.  
  
## <a name="exposing-com-components-to-c"></a>Vystavení součástí COM v C#  
 Můžete využívat komponenty modelu COM z projektu C#. Obecné kroky jsou následující:  
  
1.  Vyhledejte komponenty modelu COM pomocí a zaregistrovat ho. Použijte regsvr32.exe k registraci nebo zrušení – registrace knihovny DLL COM.  
  
2.  Přidejte do projektu odkaz na knihovnu COM součásti nebo typu.  
  
     Když přidáte odkaz na [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] používá [Tlbimp.exe (Importér knihovny)](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), což trvá knihovny typů jako vstup do výstupního sestavení vzájemné spolupráce rozhraní .NET Framework. Sestavení, také s názvem obálka volatelná na za běhu (RCW), obsahuje spravované třídy a rozhraní, které balí COM třídy a rozhraní, které jsou v knihovně typu. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]Přidá do projektu odkaz na vygenerované sestavení.  
  
3.  Vytvoření instance třídy, která je definována v RCW. To, se pak vytvoří instanci objektu COM.  
  
4.  Pomocí objektu, stejně jako použít jiné spravované objekty. Pokud je objekt uvolněn systémem uvolňování paměti, instanci objektu COM je také uvolněn z paměti.  
  
 Další informace najdete v tématu [vystavení součástí COM v rozhraní .NET Framework](../../../../docs/framework/interop/exposing-com-components.md).  
  
## <a name="exposing-c-to-com"></a>Vystavení C# do modelu COM  
 Klienti COM spotřebovat typy C#, které správně zobrazeny. Základní kroky ke zveřejnění typy C# jsou následující:  
  
1.  Přidání atributů spolupráce v projektu jazyka C#.  
  
     Pak lze zobrazit sestavení modelu COM změnou [!INCLUDE[csprcs](~/includes/csprcs-md.md)] vlastnosti projektu. Další informace najdete v tématu [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box).  
  
2.  Generovat knihovny typů COM a zaregistrovat ji COM využití.  
  
     Můžete upravit [!INCLUDE[csprcs](~/includes/csprcs-md.md)] projektu vlastnosti na automatickou registraci sestavení C# pro zprostředkovatel komunikace s objekty COM. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]používá [Regasm.exe (Nástroj registrace sestavení)](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)pomocí `/tlb` přepínač příkazového řádku, který přebírá spravované sestavení jako vstup, vytvoření knihovny typů. Popisuje této knihovny typů `public` typy v sestavení a přidá položky registru tak, aby klienti COM můžete vytvořit spravované třídy.  
  
 Další informace najdete v tématu [vystavení komponent architektury .NET Framework do modelu COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md) a [Ukázka třídy COM](../../../csharp/programming-guide/interop/example-com-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Zlepšení výkonu interoperability](https://msdn.microsoft.com/library/ms998551.aspx)  
 [Úvod do vzájemná funkční spolupráce mezi COM a .NET](https://msdn.microsoft.com/library/office/bb610378.aspx) [Úvod zprostředkovatele komunikace s objekty COM v jazyce Visual Basic](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md) [zařazování mezi spravovaných a nespravovaných kódu](../../../../docs/framework/interop/interop-marshaling.md)  
 [Spolupráce s nespravovaným kódem](../../../../docs/framework/interop/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
