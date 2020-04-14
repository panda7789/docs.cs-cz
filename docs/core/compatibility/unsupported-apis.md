---
title: Nepodporovaná rozhraní API na jádru rozhraní .NET
titleSuffix: ''
description: Zjistěte, která rozhraní API z rozhraní .NET Framework, která vždy vyvolána výjimku na .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: bd3516d9480ef42b6ea89825ba64867a3ca104e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242943"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a>Rozhraní API, která vždy vyzvou výjimky na jádru .NET

Následující rozhraní API bude <xref:System.PlatformNotSupportedException> vždy hodit na .NET Core na všech nebo podmnožinu platforem.

Tento článek uspořádá ohrožené členy rozhraní API podle oboru názvů.

> [!NOTE]
>
> - Tento článek je nedokončená. Není úplný seznam rozhraní API, které vyvolat výjimky na .NET Core.
> - Tento článek neobsahuje explicitní implementace rozhraní pro binární serializaci, které vyvolány na .NET Core. Další informace naleznete [v tématu Binary serializace in .NET Core](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>Systém

| Člen | Platformy, které hází |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Všechny |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Všechny |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Všechny |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Všechny |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Všechny |

## <a name="systemcodedomcompiler"></a>System.codedom.compiler

| Člen | Platformy, které hází |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Všechny |

## <a name="systemcollectionsspecialized"></a>System.collections.specialized

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Všechny |

## <a name="systemconfiguration"></a>System.configuration

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(všichni členové) | Všechny |

## <a name="systemconsole"></a>Systém.Konzole

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType>(pouze sada) | Linux a macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType>(pouze sada) | Linux a macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType>(pouze sada) | Linux a macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType>(získat pouze) | Linux a macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.Title?displayProperty=nameWithType>(získat pouze) | Linux a macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType>(pouze sada) | Linux a macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType>(pouze sada) | Linux a macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType>(pouze sada) | Linux a macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType>(pouze sada) | Linux a macOS |

## <a name="systemdatacommon"></a>System.data.common

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType><xref:System.NotSupportedException>(hody) | Všechny |

## <a name="systemdiagnosticsprocess"></a>System.Diagnostics.Process

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(pouze sada) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(pouze sada) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(pouze sada) | Linux a macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(získat pouze) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(pouze sada) | Linux a macOS |

## <a name="systemio"></a>System.IO

| Člen | Platformy, které hází |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |

## <a name="systemiopipes"></a>System.io.pipes

| Člen | Platformy, které hází |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(pouze sada) | Linux a macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux a macOS |

## <a name="systemmedia"></a>System.media

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |

## <a name="systemnet"></a>System.Net

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |

## <a name="systemnetnetworkinformation"></a>System.net.networkinformation

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UPW) |

## <a name="systemnetsockets"></a>System.net.sockets

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | Všechny |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Všechny |

## <a name="systemnetwebsockets"></a>Server System.Net.WebSockets

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Všechny |

## <a name="systemreflection"></a>System.reflection

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Všechny |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Všechny |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | Všechny |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Všechny |

## <a name="systemruntimecompilerservices"></a>System.runtime.compilerservices

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Všechny |

## <a name="systemruntimeinteropservices"></a>System.runtime.interopservices

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Všechny |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Všechny |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Všechny |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Všechny |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux a macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Všechny |

## <a name="systemsecurity"></a>System.security

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Všechny |

## <a name="systemsecurityclaims"></a>System.Security.Claims

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | Všechny |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | Všechny |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |

## <a name="systemsecuritycryptography"></a>System.security.cryptography

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Všechny |

## <a name="systemsecuritycryptographypkcs"></a>System.security.cryptography.pkcs

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | Všechny |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Všechny |

## <a name="systemsecuritycryptographyx509certificates"></a>System.Security.Cryptography.X509Certifikáty

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(pouze sada) | Všechny |

## <a name="systemsecurityauthenticationextendedprotection"></a>System.Security.Authentication.ExtendedProtection

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |

## <a name="systemsecuritypolicy"></a>System.security.policy

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |

## <a name="systemserviceprocessservicecontroller"></a>System.ServiceProcess.ServiceController

| Člen | Platformy, které hází |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Všechny |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Všechny |

## <a name="systemthreading"></a>System.threading

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Všechny |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Všechny |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Všechny |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Všechny |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Všechny |

## <a name="systemxml"></a>System.Xml

| Člen | Platformy, které hází |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Všechny |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Všechny |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Všechny |

## <a name="see-also"></a>Viz také

- [Nejnovější změny pro migraci z rozhraní .NET Framework na .NET Core](../compatibility/fx-core.md)
- [Binární serializace v jádru .NET Core](../../standard/serialization/binary-serialization.md#net-core)
- [Analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md)
