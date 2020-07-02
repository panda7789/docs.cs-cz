---
title: Nasazení aplikace spolupráce
description: Nasazení aplikace spolupráce, která má obvykle sestavení klienta .NET, definiční sestavení různých knihoven typů COM a registrovaných komponent modelu COM.
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
ms.openlocfilehash: 744307d4175d151d07acbedd5815e538307c8973
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617480"
---
# <a name="deploying-an-interop-application"></a>Nasazení aplikace spolupráce
Aplikace spolupráce obvykle obsahuje klientské sestavení .NET, jedno nebo více sestavení Interop představujících odlišné knihovny typů modelu COM a jednu nebo více registrovaných komponent modelu COM. Visual Studio a Windows SDK poskytují nástroje pro import a převod knihovny typů do definičního sestavení, jak je popsáno v tématu [Import knihovny typů jako sestavení](importing-a-type-library-as-an-assembly.md). Existují dva způsoby, jak nasadit aplikaci spolupráce:  
  
- Pomocí vložených typů spolupráce: počínaje .NET Framework 4 můžete instruovat kompilátor, aby vložil informace o typu ze sestavení pro spolupráci do spustitelného souboru. Kompilátor vloží pouze informace o typu, které vaše aplikace používá. Sestavení vzájemné spolupráce není nutné nasazovat do aplikace. Toto je doporučený postup.  
  
- Nasazením definičních sestavení: můžete vytvořit standardní odkaz na definiční sestavení. V takovém případě musí být definiční sestavení nasazeno s vaší aplikací. Pokud použijete tento postup a nepoužíváte privátní komponentu modelu COM, vždy se na primární definiční sestavení (PIA) publikované autorem komponenty modelu COM, kterou máte v úmyslu začlenit do spravovaného kódu, vždy odkázat. Další informace o vytváření a používání primárních sestavení vzájemné spolupráce naleznete v tématu [primární spolupracující sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
 Pokud používáte vložené typy spolupráce, nasazení je jednoduché a jednoduché. Nemusíte nic dělat zvlášť. Zbývající část tohoto článku popisuje scénáře nasazení spolupracujících sestavení s vaší aplikací.  
  
## <a name="deploying-interop-assemblies"></a>Nasazení definičních sestavení  
 Sestavení mohou mít silné názvy. Sestavení se silným názvem obsahuje veřejný klíč vydavatele, který poskytuje jedinečnou identitu. Sestavení vytvořená modulem pro [Import knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) mohou být podepsána vydavatelem pomocí možnosti **/keyfile** . Podepsaná sestavení lze instalovat do globální mezipaměti sestavení (GAC). Nepodepsaná sestavení musí být nainstalována v počítači uživatele jako soukromá sestavení.  
  
### <a name="private-assemblies"></a>Soukromá sestavení  
 Chcete-li nainstalovat sestavení, které má být použito soukromě, spustitelný soubor aplikace i sestavení spolupráce, které obsahují importované typy modelu COM, musí být nainstalovány ve stejné adresářové struktuře. Následující ilustrace znázorňuje nepodepsané sestavení vzájemné spolupráce, které má být používáno soukromě Client1.exe a Client2.exe, která se nachází v samostatných adresářích aplikace. Definiční sestavení, které se říká LOANLib.dll v tomto příkladu, je nainstalováno dvakrát.  
  
 ![Adresářová struktura a registr systému Windows](./media/deploying-an-interop-application/com-private-deployment.gif "Adresářová struktura a položky registru pro privátní nasazení")  
  
 Všechny součásti modelu COM přidružené k aplikaci musí být nainstalovány v registru systému Windows. Pokud jsou Client1.exe a Client2.exe na ilustraci nainstalovány v různých počítačích, je nutné zaregistrovat komponenty COM na obou počítačích.  
  
### <a name="shared-assemblies"></a>Sdílená sestavení  
 Sestavení, která jsou sdílená více aplikacemi, by měla být nainstalována do centralizovaného úložiště nazývaného globální mezipaměť sestavení (GAC). Klienti rozhraní .NET mají přístup ke stejné kopii definičního sestavení, které je podepsáno a nainstalováno v globální mezipaměti sestavení (GAC). Další informace o vytváření a používání primárních sestavení vzájemné spolupráce naleznete v tématu [primární spolupracující sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
- [Použití typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Kompilace projektu interoperability](compiling-an-interop-project.md)
