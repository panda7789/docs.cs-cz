---
title: Chybové zprávy nástroje Winmdexp.exe
ms.date: 03/30/2017
f1_keywords:
- WME1095
- WME1110
- WME15
- WME1094
- WME1078
- WME1080
- WME1014
- WME1025
- WME1089
- WME1111
- WME1010
- WME1013
- WME1055
- WME1005
- WME1033
- WME1003
- WME1011
- WME1046
- WME0013
- WME1032
- WME1029
- WME1048
- WME1019
- WME1106
- WME0012
- WME1017
- WME1098
- WME1039
- WME20
- WME1006
- WME1088
- WME0004
- WME10
- WME12
- WME0015
- WME0017
- WME1026
- WME1045
- WME1002
- WME1051
- WME1107
- WME1100
- WME1072
- WME1090
- WME1105
- WME1022
- WME11
- WME17
- WME1063
- WME1041
- WME1057
- WME1037
- WME1007
- WME3
- WME1096
- WME0003
- WME0006
- WME1065
- WME1102
- WME1070
- WME1113
- WME1064
- WME1061
- WME1066
- WME1018
- WME1049
- WME1027
- WME1101
- WME1058
- WME0005
- WME1083
- WME1004
- WME1073
- WME1087
- WME1077
- WME19
- WME1086
- WME1085
- WME1040
- WME8
- WME1081
- WME1023
- WME4
- WME1050
- WME7
- WME1091
- WME14
- WME0007
- WME1024
- WME1012
- WME1036
- WME0010
- WME1104
- WME1035
- WME1021
- WME1075
- WME5
- WME13
- WME1074
- WME1028
- WME0014
- WME1030
- WME1008
- WME1052
- WME1079
- WME1054
- WME1093
- WME1042
- WME2
- WME1062
- WME6
- WME1001
- WME0011
- WME16
- WME0001
- WME1020
- WME1084
- WME1103
- WME1092
- WME1
- WME0002
- WME1112
- WME1016
- WME1060
- WME0008
- WME0016
- WME1097
- WME1034
- WME1108
- WME1082
- WME1099
- WME1069
- WME1031
- WME1009
- WME1068
- WME1067
- WME1059
- WME18
- WME1038
- WME0009
- WME1109
- WME1056
- WME1076
- WME1071
- WME1044
- WME1043
- WME1053
- WME1015
- WME1047
- WME9
helpviewer_keywords:
- Winmdexp.exe, error messages
- Windows Runtime Metadata Export Tool, error messages
- error messages, Winmdexp.exe
ms.assetid: 8271973c-deba-47a6-8e5e-04ce63f146ad
ms.openlocfilehash: e99bdd106c845964f63915c87617e30eb51488f4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447310"
---
# <a name="winmdexpexe-error-messages"></a><span data-ttu-id="ac0f4-102">Chybové zprávy nástroje Winmdexp.exe</span><span class="sxs-lookup"><span data-stu-id="ac0f4-102">Winmdexp.exe Error Messages</span></span>
<span data-ttu-id="ac0f4-103">Proces sestavení volá [Winmdexp. exe (Nástroj pro export metadat prostředí Windows Runtime)](winmdexp-exe-windows-runtime-metadata-export-tool.md) při použití šablony **prostředí Windows Runtime součásti** v aplikaci Visual Studio 2012, takže se v **Seznam chyb**zobrazí chybové zprávy Winmdexp. exe.</span><span class="sxs-lookup"><span data-stu-id="ac0f4-103">The build process calls [Winmdexp.exe (Windows Runtime Metadata Export Tool)](winmdexp-exe-windows-runtime-metadata-export-tool.md) when you use the **Windows Runtime Component** template in Visual Studio 2012, so Winmdexp.exe error messages appear in the **Error List**.</span></span> <span data-ttu-id="ac0f4-104">Winmdexp. exe pracuje na modulu, který je zkompilován s možností `/target:winmdobj`.</span><span class="sxs-lookup"><span data-stu-id="ac0f4-104">Winmdexp.exe operates on a module that is compiled with the `/target:winmdobj` option.</span></span> <span data-ttu-id="ac0f4-105">Protože vyžaduje zkompilovaný modul jako vstup, jeho chybové zprávy se nezobrazí, pokud kompilace nebude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ac0f4-105">Because it requires a compiled module as input, its error messages don't appear unless compilation succeeds.</span></span>  
  
 <span data-ttu-id="ac0f4-106">Chybové zprávy jsou navržené tak, aby obsahovaly všechny informace, které potřebujete k vyřešení chybových podmínek, které jsou vykazují.</span><span class="sxs-lookup"><span data-stu-id="ac0f4-106">The error messages are designed to contain all the information you need to address the error conditions they report.</span></span> <span data-ttu-id="ac0f4-107">Některé problémy ale vyžadují více informací, než se bude vejít do zprávy.</span><span class="sxs-lookup"><span data-stu-id="ac0f4-107">However, some problems require more information than will fit in the message.</span></span> <span data-ttu-id="ac0f4-108">Další informace najdete v [části diagnostikování prostředí Windows runtimech chybových podmínek komponent](https://docs.microsoft.com/previous-versions/hh977010(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="ac0f4-108">You can find additional information in [Diagnosing Windows Runtime component error conditions](https://docs.microsoft.com/previous-versions/hh977010(v=vs.110)).</span></span>  
  
 <span data-ttu-id="ac0f4-109">Pokud vaše chyba není popsána v tomto článku a máte pocit, že zpráva neobsahuje dostatečné informace k vyřešení problému, použijte prosím odkaz na zpětnou vazbu v tomto článku a přidejte chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="ac0f4-109">If your error is not discussed in that article, and you feel that the message doesn't contain sufficient information to address the issue, please use the feedback link in that article and include the error message.</span></span> <span data-ttu-id="ac0f4-110">Případně můžete vytvořit chybu na [webu komunity vývojářů](https://developercommunity.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="ac0f4-110">Alternatively, you can file a bug at the [Developer Community website](https://developercommunity.visualstudio.com/).</span></span> <span data-ttu-id="ac0f4-111">Můžete se také podívat na Další informace o [fórech Microsoftu](https://social.msdn.microsoft.com/Forums/).</span><span class="sxs-lookup"><span data-stu-id="ac0f4-111">You can also look for more information on the [Microsoft Forums](https://social.msdn.microsoft.com/Forums/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac0f4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac0f4-112">See also</span></span>

- [<span data-ttu-id="ac0f4-113">Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)</span><span class="sxs-lookup"><span data-stu-id="ac0f4-113">Winmdexp.exe (Windows Runtime Metadata Export Tool)</span></span>](winmdexp-exe-windows-runtime-metadata-export-tool.md)
- <span data-ttu-id="ac0f4-114">[Diagnostikování chybových podmínek součásti prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/hh977010(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="ac0f4-114">[Diagnosing Windows Runtime component error conditions](https://docs.microsoft.com/previous-versions/hh977010(v=vs.110))</span></span>
