    // You can build .so file using build_for_gopax.sh

    const ffi = require('ffi');
    const ref = require('ref');

    const soFile = 'src/main/javascript/vendor/lbtc-whitelist-sign/libsecp256k1';
    const funcName = 'whitelist_sign';
    const funcInputs = [
      ref.refType(ref.types.uchar),
      ref.refType(ref.types.uchar),
      ref.refType(ref.types.uchar),
      ref.types.size_t,
      ref.refType(ref.types.uchar),
      ref.refType(ref.types.uchar),
      ref.refType(ref.types.uchar),
      ref.types.size_t,
    ];
    const funcOutput = ref.types.int;

    const sigLib = ffi.Library(soFile, {
      [funcName]: [funcOutput, funcInputs],
    });

    const oSig = new Buffer(2000);
    const iOnlinePubKeys = '223c04e8913e5bf4e884d745be9837f0908cd779372a10b629c385332a5d6cd7bf658138a02480a5243c537dac096963a198868624c21563d44bbe7e4ada6443a50dd099e6af8156d92099270492c75025a810b8ea9649d594f5f80e143fff53dc0d67af62ae6b552fa2ce3d149fc6f8c4f956e3d8719e3d724fb59bc3f7b41df63c7915e58ac11663dadd456d2f30c5814c29443fabf4e0b59952029a1932610ea1923a76ad9d46d4419ee5a2ee9f19ec2a520d3cf61a7d9358ae0c34b3afac98f884fe67a4bdc3d4cc4ed766e12dd407dfb548c360c5e10100acd9a91d58c7448dcbd408a7a55bb7ae9ab52ea01c6959606efc752f8326593d2cf3090feb17f8e9d684e644f17214234b3febc6a6bf635aa4464e9a190b99f02c50ec32c883b5e5749c003dec8292e840f7fc757f992002b4f03433fe98aff974e71b609defe1e57c412cc578e9273e80e10aab0a9fa97476cd37f32a47f3208b93ed4f2c889c5e234c992f278ac6f5edee21b3534448903a9cdd4e99e8d95ed3acf9edc24bbc316260ed38b34440885ddcd7cb9779287ac0c4a538f83d89d41e5a67c760f67c97b8602c5ef5524a2c7cdd969ef9d2cd34b15c55198f45e920f777f1f1ccb3b80e982f4c884ff51c8168967218a381ce64951a5c13fdc5b03d952ea10e74592e0a5d1f246594385bfd4d774b67226b0fa605aa10f0857b8756d98abb7202fad95330067ec5436b8ec17194f53519d22d58ba7bfca9f4c338b35696b8a0b39e41fe19ffe29d62a1abc67b745794a4bf5971c462b4424a7fc9dcb83d91207534f7385b63514324be765ba3b68c5f4ff80a9e729efeadad606c60ceef3ff19263701c153bb28b472b8127250d564b840b6f9c6fddf5662225d96ab125a2795023c1bb56f54aa4c8acb7680b67a0dac990edbb77547eceda41516e81ea1c39934e37f5db0337c00e54a1a8111889f60644af4a8962bf3dd73c1fafa8e413124566e6c4069a509f1b4a640d7c31db1669c7b01e58e194035687b56c5b2fd4d1a5999f4ad5370e827c30ad295dc788f7b3d614cd281b514459f3a28bc4dc9ec74fe85b86a308e8b11f17e9acd5f0e8a6d96d60e478013aaa0ecee5071be746d612e6b748f94ead75381a44c9d6723496bcf1c0c744c5ea9663bdb43d69a33c46e2d7bee8e61bf7998c17f03e0019e5b215505eaed7f163687051eaefa92f67dacb89014a1ba672e751d13e7da15eb5b2448b727ca6439ad30f51a5d8721f22e389f5c55e772edf47e50f4effb947d53f0ef04f95aaca7ae4419432680c67e44ffbb0c868800d8ac1b4e661b2ad577b2694c8e3d0e69f26f15aaded5f0fec19cfdc5cba0920727e8443a08df3d54ce2b25293b48aeb038811b167dd0655f97ffd8d2286cfb20976fc0ee502e84a08e84572e1f0fb9e05b1edb5bda5dc58287d87ebf2e6c81d7a1eb47598856adc0f5de84bcf614b646677b8af1ea71297ac3035c0daacb058205d006487a7e977de27e965b681a94477dcae6d8decfe6f293d38f4614b8fcea72557fe2454bdae9837a31d3e1d866d4aea963d992c40452cd27816214715d8bbdf045daefb565120b69f9b6fd76ee08a68699795059a542bd4fb0a74885808a7c82a3fd9c8a36586062558df50f262a8989a4bfd60b08c2a7b851dd67f290fb50b662039e8597d105d021e29c86c53d8ab96ebec1b3a4f70667b1a1e29bbdc889e6464d68e93a74e64188437830a5b20d10e73a5ceea91c0014d7444ed85983f4143e17c29db9d8546af8b4cb4af6390c64398cedf4124046904da2bba71e641506a72a12600cabefe7f6c499ac12b3a0964d621dd8194eb287f2477306fa244223c648da9ac7189a4c50f20651c0e3c5ba32ce66a67f6137a53a5a07eae17651e600f6f2994de83781c6402b60a880af0ce7438b7066c9034e5c440094656176dde15cfd42dd48657b32b57cd4e7a2f6621f370e8a32c9566343596bad46a05886d1cd4354df60a42a9b87b961755e2e793ac7170fa62a61b55b743234fa3f18bd3fb838cdb30012c65b10b36c12bb3d0483fc1bf0d921945ebf67b2f7b8b79583e92621f125ba3a50089280751d0be0e3ee16a1726f102c78f059505e575d357a0690dbaeea5a063db51f1035f1acf41fcf1aa08f79e12931fe9a4d6f90f95491e0dc3c94de499faf84544822eb5fd8c80591ae10ecce9b29721e8b50fe3a8edeec337ea826afd2971f4dbad56ab8484a58171e13ce3c03cebdd10e288b2225e6138507e70af535fcc052682fe66dbfb3e785a7578fccde16ea170361c3018b2d9eb70b84d735beb1ae32b48e754e26b674d8ee70a0c7424a31dbc10c1a461b5f23ddb685f705797e7c8684027178b536ac9cb65661cfe093930d5a5e8085e2b3b8e5ea938e25f588e69a26669150004dbe97cc7c28fac16691200f11849a3c5a1ca1edbaeb7570b0171b78d8533d562263e0ba1bb9fef5ab84c44a970dc601a3c19fb0cf90db047a8a28e04053e1e98c756eee23b54ff0b4289a1de3635fef05b447ee57bff89c6987252522321195983fbc6494e4842258694428d6128b61a304cbf72ce4e695c405c78aa822d343758f175a567de90f11f4cf5';
    const iOfflinePubKeys = 'c930d2ddafbb06b23184bbc85cab6b97560146edda642647204ae49848cff062c578fa28f42d1ff023c128a34af076601a84c8aa04cb67e91d3eba2db594d5af5d80c6e36652f1f2e18b78b67de00b745ecfaf5da2d4a8a81c8d812bbd80ad3f91fa803808e647685b6115cc583e77641e27497275ffa8fae713fce39ff186fd67dc9591387abf2c9e779a69d7f1a42dec775307a7bf38390a931f74885ed3f203385ad2f609da3405be0de3b168756a8e5424709650731ce4ed6f234f9f376f049eecdec603c30fceae527e6c84842d8add0268935178863ecddd200dd3866241383aac4c55998acec1d66fb2e5707ca0c8deaa602196db8ac6f19d573f2b28c5d743bdfb13b16ddac146bc7fd7616d346e7ef02d7cdb59483f743d4b88b127d39e97182531247493d3202496a23b9fa8aa3200a3dec430917d9cbd98bf7440a4efda9d16cbe52a2d7bf64cd93cdaba7fa8124a64777af27e8c923285115f07c5370bd5714acc6b734ccdeb034067c6c6e30e4ec22899527996ddbd5ec65110b2befae39b7fdb816aa97f2fda4729e9b5e2e337472bc86acd157c338e4488b9649d4efe329ff85049fff05a23518d4b9320119d4ea78b0215256ffc4669a48c619087bbe148187923688286e4d572a010c4545f8bd09c8b4152319e9963b74506f95bf563699bdf84894e6469eadd6702e0e15a3e558d259fa9162199b3556a8246bb66d2c108d03bcf380a92b1f8b57ba6bdcb870ca45cd0d551431414882fc163e19c638a72bf03c1b220635a81c53c847f17487881b79a73c7f99e7f7099d2c7a256af058c7dd4e6d94545fa134bb35c7c4bc2deb8cf5509371318edb2d84d784c41761044e2bc3314c54e8c0fe66503786309dabca2ba34fd23c2a296d4e57d9c994a3fbd1922d94f13b5012b44ac77fb4d5cb64ff33ab81ef4476ea5e27bbdc395d56019754008d0ce9deaa0df849fc6f52c794a422b2f70275b2ea26f6d231cf424029aee95536b7639b0cb2c25f0818fa72a58c1680ee8bca4396b15471718c90af0a8cf01db26f6ebc325d56f11a5915fdb547fd4bb145eaba4ae8301e29aab686b691770761fbb47ef25a023b86659c5b404eb4d1681dce133e09cea6cd9d5d87b083ef0470301649acaab024df7818a851edf428596b21aba8867f67e020483784e259dcf0440ee82de2458ec523ce85924403eb292ff0c0f30a80c1f6dac78401eefbb0f12d264e9deec4a177ce471c7fd3bb0380cc40ad4c9200f94e17498d599f0cdb5873a0aeb713633e3229d2d12eee41b7ebc41cf7ebafcd193f265d22bfb6eac4408f96d054661283f51e2e52bdf3b87215aeab918ae910860a929a57c8d9ad729fc158ba774a92adc9c6f16a4a1dd6a90c0bda107f835cff9412e405d0e97329faedbb580a85330d3787d832395211839d45b5c6dd274c1246704b3dd0c2eae47f9c45a29b954626293c6520e22fd9b24f8aa3d96c2fc6f1ea6977c228a4fe386af1733e85279d57249ca0634cc2d9c589c276b6d9a5cdffd2bd558d9230d1555a4fb2e6b826e06d226f20ed5fbd314ce415cbf22fd9bc5792e5f2d67a80000f57cf027515a1909d4225affe15ecf5026feac19ae3c1a75862df669e85f25be74cec6dcffabff4fcb92512336fb54e38f5d7c02cb7fd6b4829b6185a630e3192e24e93a37fec591e7c082f6dac214252b386bf9c747abe7a866fd976089070ffcc0f52c889245f2a77b9332e89c8e95758958eb83e9cf9cf06307d59ea616bc001c09542600cdda9a97d870888cae8c9115cb9bad3a0f5786a25b4863399d9b6e1f04fba7603d01d97a5a02000872b31305310cddc69e08a6020ee28480a19ec49d631f51790942006d3be3c1ff7ca86bd4c012529a9544be8f9974ff5469c480877dff491134220c41e0f84f23fedc67a6c472a3def9d349ada9cf59e5259503869868d859771ef9119c69729566297c2886b0bee6be882c8568dea28856727e2da1332a9b7176347eac4390fa75bae193dbf22085cf374f4504bb184b87366bc3d6bd82c8df72314e4b470b33deafde427bb398045f42bdcc5b14db02d79d2d871809f7f18b9575802ab96970400c369f55a56194f70114d1986a2e510579c8cc63833d39e8d1a5bd88341b3ea356a5ac37dd6c04f9ed6a1bb78bca5d3a9ef61391e9cc87cc3cb17c16becfdec91f867ce8d949f0d70cbaa1ddb5595961ac5def5c52965743fd6664f9c96a5f7ef91a7f0226353920f015eebcac283caf1e354ddc3a4c4a71724fd6f539e0dc55131d84c6fcefbf8168d509d295bf6258d6e4fbe4c9e4917062ab65045a0661e9e03387b43a59f6ac74a5f2b3e0cd1fe377e185db077e30c978fd31f6ea7354e100a047634bf15156a68b22578c57f6ee2e38d248b79d3d8b3e07562ab68508adca3f6eea9a2226ade88d2b53f98a587046ab740e1f1c0430d89a864a0af3277965dc1ebe55487a62d3d508423afa8e70b0ae63d5dbc0626db6c850083c6ea2fc3a835b33a278901d57203d2b5b581f562af324e5bba2c2e59267967109a110dd2c65811edc1f9586182b9911f6d1e951d6bff8d41324b769d7ce6920ea2bc152c3c03cae769a9019';
    const iNumKey = 29;
    const iSubPubKey = 'a55ec1dbced2ef75b6b6492c27c5c1bf431546438a1b4a67ec58673219e71e2bfcd1919cdaebb0c91d9939428a03bb37c3addd9701a2e25010d6524189565268';
    const iOnlineSecKey = 'baf941d9888cb1fa6f204e372ee42788fc3fa7f4366244c69b28c84a07c1424d';
    const iSummedSecKey = 'a83188f45d9c18c64f9f19257744452b2ea7dfb951906996e88a7dcf0f14887f';
    const iIndex = 0;

    sigLib[funcName](
      oSig,
      new Buffer(iOnlinePubKeys, 'hex'),
      new Buffer(iOfflinePubKeys, 'hex'),
      iNumKey,
      new Buffer(iSubPubKey, 'hex'),
      new Buffer(iOnlineSecKey, 'hex'),
      new Buffer(iSummedSecKey, 'hex'),
      iIndex,
    );
    const sig = oSig.toString('hex');
    console.log('sig', sig);